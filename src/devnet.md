# Subspace Devnet

## Description

Subspace Devnet is a network setup which can be quickly launched by any developer to see the network running in their local system.

## Instruction

There are genesis accounts (holding balances) for Nova (EVM-based) chain:

> With `--chain dev` you can find some funds in the dev account:

```sh
[
    {
        "name": "Alith",
        "p": "0x02509540919faacf9ab52146c9aa40db68172d83777250b28e4679176e49ccdd9f",
        "s": "0x5fb92d6e98884f76de468fa3f6278f8807c48bebc13595d45af5bdc4da702133"
    },
    {
        "name": "Baltathar",
        "p": "0x033bc19e36ff1673910575b6727a974a9abd80c9a875d41ab3e2648dbfb9e4b518",
        "s": "0x8075991ce870b93a8870eca0c0f91913d12f47948ca0fd25b49c6fa7cdbeee8b"
    },
    {
        "name": "Charleth",
        "p": "0x0234637bdc0e89b5d46543bcbf8edff329d2702bc995e27e9af4b1ba009a3c2a5e",
        "s": "0x0b6e18cafb6ed99687ec547bd28139cafdd2bffe70e6b688025de6b445aa5c5b"
    },
    {
        "name": "Dorothy",
        "p": "0x02a00d60b2b408c2a14c5d70cdd2c205db8985ef737a7e55ad20ea32cc9e7c417c",
        "s": "0x39539ab1876910bbf3a223d84a29e28f1cb4e2e456503e7e91ed39b2e7223d68"
    }
]
```

### 1. Download subspace node binary

Download the "subspace-node-macos-aarch64-gemini-3h-2024-may-06.zip" from the [releases page](https://github.com/subspace/subspace/releases/tag/gemini-3h-2024-may-06). And then extract.

### 2. Insert operator signing key for each domain

> From here onwards, `BASE-PATH` should be same.

- for domain-0: `./subspace-node-macos-aarch64-gemini-3h-2024-may-06 domain key insert --domain-id 0 --base-path <BASE-PATH> --keystore-suri "//Alice"`

```sh
$ ./subspace-node-macos-aarch64-gemini-3h-2024-may-06 domain key insert --domain-id 0 --base-path ./subspace-node --keystore-suri "//Alice"
2024-05-09T14:54:56.054072Z  INFO subspace_node::commands::domain_key: Success
```

- for domain-1: `./subspace-node-macos-aarch64-gemini-3h-2024-may-06 domain key insert --domain-id 1 --base-path <BASE-PATH> --keystore-suri "//Bob"`

```sh
$ ./subspace-node-macos-aarch64-gemini-3h-2024-may-06 domain key insert --domain-id 1 --base-path ./subspace-node --keystore-suri "//Bob"
2024-05-09T14:56:41.749115Z  INFO subspace_node::commands::domain_key: Success
```

### 3. Start the node

```sh
$ 2024-05-13T14:15:42.375012Z  INFO subspace_node::commands::run: 💾 Node path: ./subspace-node
2024-05-13T14:15:42.796037Z  INFO Consensus: sc_service::client::client: 🔨 Initializing Genesis block/state (state: 0x5623…7c80, header-hash: 0x31ce…8015)
2024-05-13T14:15:43.233581Z  INFO Consensus: subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=false peer_id=12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g protocol_version=/subspace/2/31cee242859362151def6b3bb64fd609151d6b0a319879e8f7f23501e59f8015
2024-05-13T14:15:43.236285Z  INFO Consensus: libp2p_swarm: local_peer_id=12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.237548Z  INFO Consensus: subspace_service: Subspace networking initialized: Node ID is 12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.239439Z  INFO Consensus: subspace_service: DSN listening on /ip4/127.0.0.1/tcp/30433/p2p/12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.239805Z  INFO Consensus: subspace_service: DSN listening on /ip6/::1/tcp/30433/p2p/12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.239867Z  INFO Consensus: subspace_service: DSN listening on /ip4/192.168.0.100/tcp/30433/p2p/12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.240920Z  WARN Consensus: sc_service::config: Using default protocol ID "sup" because none is configured in the chain specs
2024-05-13T14:15:43.241560Z  INFO Consensus: block_relay: relay::consensus block server: starting
2024-05-13T14:15:43.242694Z  INFO Consensus: sub-libp2p: 🏷  Local node identity is: 12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:43.246104Z  INFO Consensus: sc_consensus_subspace::archiver: Starting archiving from genesis
2024-05-13T14:15:43.246141Z  INFO Consensus: sc_consensus_subspace::archiver: Archiving already produced blocks 0..=0
2024-05-13T14:15:49.920853Z  INFO Consensus: subspace: 🧑‍🌾 Starting Subspace Authorship worker
2024-05-13T14:15:49.936584Z  INFO Consensus: sc_sysinfo: 💻 Operating system: macos
2024-05-13T14:15:49.936618Z  INFO Consensus: sc_sysinfo: 💻 CPU architecture: aarch64
2024-05-13T14:15:49.936854Z  INFO Consensus: sc_service::builder: 📦 Highest known block at #0
2024-05-13T14:15:49.954651Z  INFO Consensus: sc_rpc_server: Running JSON-RPC server: addr=127.0.0.1:9944, allowed origins=["*"]
2024-05-13T14:15:49.975095Z  INFO Consensus: message::relayer: Starting relayer for chain: Consensus
2024-05-13T14:15:49.975096Z  INFO Consensus: domain_message_listener: Starting transaction listener for Chain: Consensus
2024-05-13T14:15:50.178346Z  INFO Domain: sc_service::client::client: 🔨 Initializing Genesis block/state (state: 0x72ee…08b2, header-hash: 0x43c7…04f4)
2024-05-13T14:15:50.178913Z  INFO Domain: sub-libp2p: 🏷  Local node identity is: 12D3KooWEvM9rD2unb5HDL2zJaStMcnBD8sYa91qVvhopxhi6h3g
2024-05-13T14:15:50.183043Z  INFO Domain: sc_sysinfo: 💻 Operating system: macos
2024-05-13T14:15:50.183048Z  INFO Domain: sc_sysinfo: 💻 CPU architecture: aarch64
2024-05-13T14:15:50.183051Z  INFO Domain: sc_service::builder: 📦 Highest known block at #0
2024-05-13T14:15:50.183433Z  INFO Domain: sc_rpc_server: Running JSON-RPC server: addr=127.0.0.1:56904, allowed origins=["*"]
2024-05-13T14:15:50.183687Z  INFO Domain: message::relayer: Starting relayer for chain: Domain(DomainId(1))
2024-05-13T14:15:50.183689Z  INFO Domain: domain_message_listener: Starting transaction listener for Chain: Domain(DomainId(1))
2024-05-13T14:15:50.184139Z  INFO Domain: domain_client_operator::domain_worker: 👷 Running as Operator[1]...
2024-05-13T14:15:50.872513Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 1
2024-05-13T14:15:50.873865Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(1)
2024-05-13T14:15:50.877158Z  INFO Domain: runtime::domains: Submitted bundle from slot 1, extrinsics: 0
2024-05-13T14:15:51.826666Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 2
2024-05-13T14:15:51.826981Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(2)
2024-05-13T14:15:51.828710Z  INFO Domain: runtime::domains: Submitted bundle from slot 2, extrinsics: 0
2024-05-13T14:15:52.783496Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 3
2024-05-13T14:15:52.783872Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(3)
2024-05-13T14:15:52.785595Z  INFO Domain: runtime::domains: Submitted bundle from slot 3, extrinsics: 0
2024-05-13T14:15:53.738186Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 4
2024-05-13T14:15:53.738599Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(4)
2024-05-13T14:15:53.740412Z  INFO Domain: runtime::domains: Submitted bundle from slot 4, extrinsics: 0
2024-05-13T14:15:54.691409Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 5
2024-05-13T14:15:54.691759Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(5)
2024-05-13T14:15:54.693490Z  INFO Domain: runtime::domains: Submitted bundle from slot 5, extrinsics: 0
2024-05-13T14:15:54.973561Z  INFO Consensus: substrate: 💤 Idle (0 peers), best: #0 (0x31ce…8015), finalized #0 (0x31ce…8015), ⬇ 0 ⬆ 0
2024-05-13T14:15:55.188735Z  INFO Domain: substrate: 💤 Idle (0 peers), best: #0 (0x43c7…04f4), finalized #0 (0x43c7…04f4), ⬇ 0 ⬆ 0
2024-05-13T14:15:55.642545Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 6
2024-05-13T14:15:55.642974Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(6)
2024-05-13T14:15:55.644820Z  INFO Domain: runtime::domains: Submitted bundle from slot 6, extrinsics: 0
2024-05-13T14:15:56.596494Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 7
2024-05-13T14:15:56.596864Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(7)
2024-05-13T14:15:56.598703Z  INFO Domain: runtime::domains: Submitted bundle from slot 7, extrinsics: 0
2024-05-13T14:15:57.552400Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 8
2024-05-13T14:15:57.552823Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(8)
2024-05-13T14:15:57.554700Z  INFO Domain: runtime::domains: Submitted bundle from slot 8, extrinsics: 0
2024-05-13T14:15:58.506897Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 9
2024-05-13T14:15:58.507494Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(9)
2024-05-13T14:15:58.509424Z  INFO Domain: runtime::domains: Submitted bundle from slot 9, extrinsics: 0
2024-05-13T14:15:59.464422Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 10
2024-05-13T14:15:59.464883Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(10)
2024-05-13T14:15:59.466818Z  INFO Domain: runtime::domains: Submitted bundle from slot 10, extrinsics: 0
2024-05-13T14:15:59.976549Z  INFO Consensus: substrate: 💤 Idle (0 peers), best: #0 (0x31ce…8015), finalized #0 (0x31ce…8015), ⬇ 0 ⬆ 0
2024-05-13T14:16:00.193916Z  INFO Domain: substrate: 💤 Idle (0 peers), best: #0 (0x43c7…04f4), finalized #0 (0x43c7…04f4), ⬇ 0 ⬆ 0
2024-05-13T14:16:00.424523Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 11
2024-05-13T14:16:00.424854Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(11)
2024-05-13T14:16:00.426652Z  INFO Domain: runtime::domains: Submitted bundle from slot 11, extrinsics: 0
2024-05-13T14:16:01.385793Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 12
2024-05-13T14:16:01.386110Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(12)
2024-05-13T14:16:01.387812Z  INFO Domain: runtime::domains: Submitted bundle from slot 12, extrinsics: 0
```

Note down:

```text
Consensus RPC node: ws://127.0.0.1:9944
Domain RPC node: ws://127.0.0.1:56904
```

Open PolkadotJS explorer in 2 tabs & feed this url to see the blocks.

### 4. Start the farmer

a. Download the "subspace-farmer-macos-aarch64-gemini-3h-2024-may-06.zip" from the [releases page](https://github.com/subspace/subspace/releases/tag/gemini-3h-2024-may-06). And then extract.
b. Generate an account

```sh
subkey generate
Secret phrase:       fine mandate shoot dilemma relax pelican execute diary yard logic crater critic
  Network ID:        substrate
  Secret seed:       0x0a69da362053d06650e374ec820ce74b7d236d9f8b03a723d628ced69566956a
  Public key (hex):  0x2af51d7252bac3a5e848b48108f582ab6ac740d93ffa6ec440831633a511aa48
  Account ID:        0x2af51d7252bac3a5e848b48108f582ab6ac740d93ffa6ec440831633a511aa48
  Public key (SS58): 5D32gYpecXVimTYXcULattG1RREc2uL8dzMa5XDdDdhVxC7e
  SS58 Address:      5D32gYpecXVimTYXcULattG1RREc2uL8dzMa5XDdDdhVxC7e
```

c. Get the ss58 prefixed-address of the address:

Go to Developer >> Utilities >> Convert address in "PolkadotJS explorer".

![](img/convert_address_ss58_subspace.png)

```sh
5D32gYpecXVimTYXcULattG1RREc2uL8dzMa5XDdDdhVxC7e

st7EWm3Y7KBwwX5X7Udz574k5A2d4ybpPfFqJN5Bv1Z2bnnh7
```

d. Start the farmer node

```sh
./subspace-farmer-macos-aarch64-gemini-3h-2024-may-06 farm path=./subspace-farm,size=2GB --reward-address st7EWm3Y7KBwwX5X7Udz574k5A2d4ybpPfFqJN5Bv1Z2bnnh7 --node-rpc-url ws://127.0.0.1:9944
2024-05-11T12:31:26.984409Z  INFO subspace_farmer::commands::farm: Connecting to node RPC url=ws://127.0.0.1:9944
2024-05-11T12:31:26.986721Z  INFO subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=false peer_id=12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ protocol_version=/subspace/2/31cee242859362151def6b3bb64fd609151d6b0a319879e8f7f23501e59f8015
2024-05-11T12:31:26.986891Z  INFO libp2p_swarm: local_peer_id=12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.313077Z  INFO subspace_farmer::commands::farm: Preparing plotting thread pools plotting_thread_pool_core_indices=[CpuCoreSet { cores: CpuSet(0-15), .. }] replotting_thread_pool_core_indices=[CpuCoreSet { cores: CpuSet(0-7), .. }]
2024-05-11T12:31:27.316206Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plot_cache: Checking plot cache contents, this can take a while
2024-05-11T12:31:27.316293Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plot_cache: Finished checking plot cache contents
2024-05-11T12:31:27.316854Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm: Benchmarking faster proving method
2024-05-11T12:31:27.711433Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm: Faster proving method found fastest_mode=ConcurrentChunks
2024-05-11T12:31:27.726658Z  INFO {farm_index=0}: subspace_farmer::commands::farm: Farm 0:
2024-05-11T12:31:27.726679Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   ID: 01HXGKVSM890AZSKX898ZVVH0R
2024-05-11T12:31:27.726682Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Genesis hash: 0x31cee242859362151def6b3bb64fd609151d6b0a319879e8f7f23501e59f8015
2024-05-11T12:31:27.726685Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Public key: 0xba2ef87a59dd70491c564038d84682286dcda4cf0b22cd53ffd272cfaeb2df56
2024-05-11T12:31:27.726690Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Allocated space: 1.9 GiB (2.0 GB)
2024-05-11T12:31:27.726697Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Directory: ./subspace-farm
2024-05-11T12:31:27.726711Z  INFO subspace_farmer::commands::farm: Collecting already plotted pieces (this will take some time)...
2024-05-11T12:31:27.726728Z  INFO subspace_farmer::farmer_cache: Initializing piece cache
2024-05-11T12:31:27.726876Z  INFO subspace_farmer::commands::farm: Finished collecting already plotted pieces successfully
2024-05-11T12:31:27.726967Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::farming: Subscribing to slot info notifications
2024-05-11T12:31:27.726979Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Subscribing to reward signing notifications
2024-05-11T12:31:27.727004Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip4/127.0.0.1/tcp/30533/p2p/12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.727110Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip6/::1/tcp/30533/p2p/12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.727117Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip4/192.168.29.200/tcp/30533/p2p/12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.727121Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip6/2405:201:8008:e8d0:1406:54e6:1219:8ee6/tcp/30533/p2p/12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.727151Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip6/2405:201:8008:e8d0:18e9:bb4e:c30e:f48a/tcp/30533/p2p/12D3KooWCsVHBbcdgixo1VHPYfjnZaFeahx2oR8YsAz5KMXzJRfZ
2024-05-11T12:31:27.727209Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plotting: Subscribing to archived segments
2024-05-11T12:31:27.878214Z  INFO subspace_farmer::farmer_cache: Synchronizing piece cache
2024-05-11T12:31:27.878594Z  INFO subspace_farmer::farmer_cache: Finished piece cache synchronization
2024-05-11T12:31:31.348803Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x3c8c52e711f873df17c6e914a094d201216b4fbf7655ad4bb0411ff191e400ca
2024-05-11T12:31:34.147648Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x51deefd24576a439d109422271351b8ce10564335d2bbd85d50f9ba39a492a14
2024-05-11T12:31:42.366457Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xe6089a329ebbbce6bdf6315b5de191af4df76acfd98734ccb37d2841917a0c57
2024-05-11T12:31:43.038860Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xf400ff691fd640afc6573e5e9fa4a8d842dc496d4200e32c119a123d87a05dd1
2024-05-11T12:31:50.508517Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xaa36a8557c562e7d57d1225b8d7bccde9ef671617724e663c0f9df4033c20716
2024-05-11T12:31:52.547535Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xa8a526e36fb33841c99cb4d2be6f92480c75a6c687be6927f5c6a9747159a3d2
```

Now, the block starts producing.

> NOTE: In a substrate-node-template, the blocks are produced automatically based on the consensus algorithm. Here, in subspace, it is driven by farming i.e. your space pledged. More the farmers, merrier it is for Subspace blockchain in terms of decentralization.

> NOTE: Until the farmer node's initial plotting is complete, the subspace node will not produce blocks. In the subspace node, the 2 flags allow farmer to do `reward_signing`: `--farmer` and `--timekeeper`.

### 5. DONE! 🎉

Now, you can send a pallet tx to your subspace consensus chain using some CLI tool like `subxt` or script.

Also, you can test the domain-1 i.e. Nova (EVM-based) chain by sending txs using CLI tool like `foundry` or script (Solidity, TS, Rust).
