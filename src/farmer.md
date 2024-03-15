# Farmer

## Overview

## Build

To build a subspace node binary, do this:

```sh
cargo r -r --bin subspace-farmer
```

## Run

To run a farmer:

```sh
./target/release/subspace-farmer farm path=YOUR_FARM_PATH,size=YOUR_FARM_SIZE --reward-address YOUR_REWARD_ADDRESS
```

<details><summary>Details:</summary>

```sh
$ ./target/release/subspace-farmer farm path=/Users/abhi3700/subspace-node/farm0,size=2GB --reward-address stAX2ZuGgXeybRNoRq8JSkjK541j8DVHTcgPZ7bNWUvVCCvho                                                     ⏎
./target/debug/subspace-farmer farm path=/Users/abhi3700/subspace-node/farm0,size=2GB --reward-address stAX2ZuGgXeybRNoRq8JSkjK541j8DVHTcgPZ7bNWUvVCCvho                                                     ⏎
2024-03-15T13:16:28.435168Z  INFO subspace_farmer::commands::farm: Connecting to node RPC url=ws://127.0.0.1:9944
2024-03-15T13:16:28.463705Z  INFO subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=false peer_id=12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR protocol_version=/subspace/2/0c121c75f4ef450f40619e1fca9d1e8e7fbabc42c895bc4790801e85d5a91c34
2024-03-15T13:16:28.466006Z  INFO libp2p_swarm: local_peer_id=12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:16:28.990369Z  INFO {disk_farm_index=0}: subspace_farmer::single_disk_farm::plot_cache: Checking plot cache contents
2024-03-15T13:16:28.999509Z  INFO subspace_farmer::single_disk_farm: Benchmarking faster proving method
Single disk farm 0:
  ID: 01HS141PX1YWHC5JXH7HM3K47K
  Genesis hash: 0x0c121c75f4ef450f40619e1fca9d1e8e7fbabc42c895bc4790801e85d5a91c34
  Public key: 0x587d5a17b734608dc8de85fd639fbe03b16da5883238e0742b50cd0e756a9a02
  Allocated space: 1.9 GiB (2.0 GB)
  Directory: /Users/abhi3700/subspace-node/farm0
2024-03-15T13:17:55.779541Z  INFO subspace_farmer::commands::farm: Collecting already plotted pieces (this will take some time)...
2024-03-15T13:17:55.779573Z  INFO subspace_farmer::commands::farm: Finished collecting already plotted pieces successfully
2024-03-15T13:17:55.779591Z  INFO subspace_farmer::farmer_cache: Initializing piece cache
2024-03-15T13:17:55.782656Z  INFO {disk_farm_index=0}: subspace_farmer::single_disk_farm::farming: Subscribing to slot info notifications
2024-03-15T13:17:55.784536Z  INFO {disk_farm_index=0}: subspace_farmer::reward_signing: Subscribing to reward signing notifications
2024-03-15T13:17:55.786998Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip4/127.0.0.1/udp/30533/quic-v1/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.787912Z  INFO {disk_farm_index=0}: subspace_farmer::single_disk_farm::plotting: Subscribing to archived segments
2024-03-15T13:17:55.789545Z  INFO subspace_farmer::farmer_cache: Synchronizing piece cache
2024-03-15T13:17:55.790773Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip6/::1/udp/30533/quic-v1/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.790841Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip4/192.168.0.100/udp/30533/quic-v1/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.790911Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip4/127.0.0.1/tcp/30533/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.790966Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip6/::1/tcp/30533/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.791006Z  INFO subspace_farmer::commands::farm::dsn: DSN listening on /ip4/192.168.0.100/tcp/30533/p2p/12D3KooWQjoMgvXiASNLWgHDUjAtzL4ypYaBk8TRfFHxSxfdJrpR
2024-03-15T13:17:55.857646Z  INFO {disk_farm_index=0}: subspace_farmer::single_disk_farm::plotting: Plotting sector (0.00% complete) sector_index=0
```

</details>

> Need to wait for node sync first before farming starts.

To get the farm info, run:

```sh
$ ./target/release/subspace-farmer info
2024-03-15T13:27:59.993326Z  INFO subspace_farmer: No farm was specified, so there is nothing to do
```

To wipe the farm, run:

```sh
./target/release/subspace-farmer wipe FARM_PATH
```

## Recipes

### How a farmer type is defined?

```rust
use subspace_proof_of_space::chia::ChiaTable;

/// Subspace farmer type
pub type Farmer = sdk_farmer::Farmer<ChiaTable>;
```

### How to define a farm/plot?

A farm is defined via a `FarmDescription` struct. It contains the following fields:

- `directory`: Path of the farm
- `space_pledged`: Space which you want to pledge for the farm

```rust
//! Source code at file: https://github.com/subspace/subspace-sdk/blob/main/farmer/src/lib.rs

/// Description of the farm
#[derive(Debug, Clone, PartialEq, Eq, Deserialize, Serialize)]
#[non_exhaustive]
pub struct FarmDescription {
    /// Path of the farm
    pub directory: PathBuf,
    /// Space which you want to pledge
    pub space_pledged: ByteSize,
}
```

- Here, the struct can be printed/logged, cloned, compared for equality, deserialized and serialized.
- The struct is non-exhaustive, which means that the struct may have additional fields added to it in the future without breaking backwards compatibility. It is a way to signal to users of the struct that they should not rely on the struct having only the fields defined in its current version.

### What are the associated methods of a farm/plot?

A farm has the following associated methods:

- `new`: Construct Farm description
- `wipe`: Wipe all the data from the farm

The functions are defined like this:

```rust
//! Source code at file: https://github.com/subspace/subspace-sdk/blob/main/farmer/src/lib.rs

impl FarmDescription {
    /// Construct Farm description
    pub fn new(directory: impl Into<PathBuf>, space_pledged: ByteSize) -> Self {
        Self { directory: directory.into(), space_pledged }
    }

    /// Wipe all the data from the farm
    pub async fn wipe(self) -> io::Result<()> {
        tokio::fs::remove_dir_all(self.directory).await
    }
}
```

### How to farm?

This has been abstracted in the `pulsar` tool. The `farm` command is responsible for farming. [Chapter](./pulsar/farm.md).
