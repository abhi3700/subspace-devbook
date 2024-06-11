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

> NOTE: Previously, there were 2 domains: Auto ID, EVM chain Nova. But now, there is only 1 domain: Nova.

> From here onwards, `BASE-PATH` should be same.

#### ~~OLD~~

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

#### NEW

Not required as in the `./subspace-node`, already `--keystore-suri "//Bob"` is passed.

### 3. Start the node

```sh
$ ./subspace-node-macos-aarch64-gemini-3h-2024-jun-11 run --dev --farmer --timekeeper --base-path ./subspace-node --state-pruning archive-canonical --blocks-pruning archive-canonical  --rpc-cors all --force-synced --force-authoring -- --domain-id 0 --operator-id 0 --state-pruning archive-canonical --blocks-pruning archive-canonical --rpc-cors all --keystore-suri "//Bob"
2024-06-11T12:06:07.107668Z  INFO subspace_node::commands::run: Subspace
2024-06-11T12:06:07.107688Z  INFO subspace_node::commands::run: ✌️  version 0.1.0-7d1f1fe8bef
2024-06-11T12:06:07.107690Z  INFO subspace_node::commands::run: ❤️  by Subspace Labs <https://subspace.network>
2024-06-11T12:06:07.107692Z  INFO subspace_node::commands::run: 📋 Chain specification: Subspace development
2024-06-11T12:06:07.107693Z  INFO subspace_node::commands::run: 🏷  Node name: outstanding-sail-1044
2024-06-11T12:06:07.107696Z  INFO subspace_node::commands::run: 💾 Node path: ./subspace-node
2024-06-11T12:06:07.530592Z  INFO Consensus: sc_service::client::client: 🔨 Initializing Genesis block/state (state: 0xd7c4…e2a8, header-hash: 0x0180…146f)
2024-06-11T12:06:07.848287Z  INFO Consensus: subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=true peer_id=12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E protocol_version=/subspace/2/0180586b2cf95c03465a0705f54907c52f99f3e4aec786cca6f8c6a9a3f4146f
2024-06-11T12:06:07.848563Z  INFO Consensus: libp2p_swarm: local_peer_id=12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.848855Z  INFO Consensus: subspace_service: Subspace networking initialized: Node ID is 12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.848959Z  INFO Consensus: subspace_service: DSN listening on /ip4/127.0.0.1/tcp/30433/p2p/12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.849011Z  INFO Consensus: subspace_service: DSN listening on /ip6/::1/tcp/30433/p2p/12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.849032Z  INFO Consensus: subspace_service: DSN listening on /ip4/192.168.0.101/tcp/30433/p2p/12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.849067Z  WARN Consensus: sc_service::config: Using default protocol ID "sup" because none is configured in the chain specs
2024-06-11T12:06:07.849139Z  INFO Consensus: block_relay: relay::consensus block server: starting
2024-06-11T12:06:07.849282Z  INFO Consensus: sub-libp2p: 🏷  Local node identity is: 12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:07.850281Z  INFO Consensus: sc_consensus_subspace::archiver: Starting archiving from genesis
2024-06-11T12:06:07.850307Z  INFO Consensus: sc_consensus_subspace::archiver: Archiving already produced blocks 0..=0
2024-06-11T12:06:13.260062Z  INFO Consensus: subspace: 🧑‍🌾 Starting Subspace Authorship worker
2024-06-11T12:06:13.268748Z  INFO Consensus: sc_sysinfo: 💻 Operating system: macos
2024-06-11T12:06:13.268762Z  INFO Consensus: sc_sysinfo: 💻 CPU architecture: aarch64
2024-06-11T12:06:13.268764Z  INFO Consensus: sc_service::builder: 📦 Highest known block at #0
2024-06-11T12:06:13.278829Z  INFO Consensus: sc_rpc_server: Running JSON-RPC server: addr=127.0.0.1:9944, allowed origins=["*"]
2024-06-11T12:06:13.290144Z  INFO Consensus: message::relayer: Starting relayer for chain: Consensus
2024-06-11T12:06:13.290164Z  INFO Consensus: domain_message_listener: Starting transaction listener for Chain: Consensus
2024-06-11T12:06:13.461464Z  INFO Domain: sc_service::client::client: 🔨 Initializing Genesis block/state (state: 0x3f57…f346, header-hash: 0x8c8e…2f40)
2024-06-11T12:06:13.462001Z  INFO Domain: sub-libp2p: 🏷  Local node identity is: 12D3KooWDh6WjwAh5MMuv5Yxtn3SoWAoaKsMPRTTAykvrhGvVm7E
2024-06-11T12:06:13.465395Z  INFO Domain: sc_sysinfo: 💻 Operating system: macos
2024-06-11T12:06:13.465403Z  INFO Domain: sc_sysinfo: 💻 CPU architecture: aarch64
2024-06-11T12:06:13.465405Z  INFO Domain: sc_service::builder: 📦 Highest known block at #0
2024-06-11T12:06:13.465627Z  INFO Domain: sc_rpc_server: Running JSON-RPC server: addr=127.0.0.1:63459, allowed origins=["*"]
2024-06-11T12:06:13.465813Z  INFO Domain: domain_client_operator::domain_worker: 👷 Running as Operator[0]...
2024-06-11T12:06:13.465839Z  INFO Domain: message::relayer: Starting relayer for chain: Domain(DomainId(0))
2024-06-11T12:06:13.465848Z  INFO Domain: domain_message_listener: Starting transaction listener for Chain: Domain(DomainId(0))
2024-06-11T12:06:13.955988Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 1
2024-06-11T12:06:13.956425Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(1)
2024-06-11T12:06:13.958110Z  INFO Domain: runtime::domains: Submitted bundle from slot 1, extrinsics: 0
2024-06-11T12:06:14.621591Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 2
2024-06-11T12:06:14.622075Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(2)
2024-06-11T12:06:14.623690Z  INFO Domain: runtime::domains: Submitted bundle from slot 2, extrinsics: 0
2024-06-11T12:06:15.289121Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 3
2024-06-11T12:06:15.289610Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(3)
2024-06-11T12:06:15.291197Z  INFO Domain: runtime::domains: Submitted bundle from slot 3, extrinsics: 0
2024-06-11T12:06:15.964144Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 4
2024-06-11T12:06:15.964517Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(4)
2024-06-11T12:06:15.965949Z  INFO Domain: runtime::domains: Submitted bundle from slot 4, extrinsics: 0
2024-06-11T12:06:16.631683Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 5
2024-06-11T12:06:16.631983Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(5)
2024-06-11T12:06:16.633396Z  INFO Domain: runtime::domains: Submitted bundle from slot 5, extrinsics: 0
2024-06-11T12:06:17.303384Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 6
2024-06-11T12:06:17.303703Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(6)
2024-06-11T12:06:17.305029Z  INFO Domain: runtime::domains: Submitted bundle from slot 6, extrinsics: 0
2024-06-11T12:06:17.984517Z  INFO Domain: domain_client_operator::domain_bundle_producer: 📦 Claimed bundle at slot 7
2024-06-11T12:06:17.984821Z  INFO Domain: domain_client_operator::domain_bundle_producer: 🔖 Producing bundle at slot Slot(7)
2024-06-11T12:06:17.986123Z  INFO Domain: runtime::domains: Submitted bundle from slot 7, extrinsics: 0
2024-06-11T12:06:18.291965Z  INFO Consensus: substrate: 💤 Idle (0 peers), best: #0 (0x0180…146f), finalized #0 (0x0180…146f), ⬇ 0 ⬆ 0
2024-06-11T12:06:18.470960Z  INFO Domain: substrate: 💤 Idle (0 peers), best: #0 (0x8c8e…2f40), finalized #0 (0x8c8e…2f40), ⬇ 0 ⬆ 0
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
./subspace-farmer-macos-aarch64-gemini-3h-2024-jun-11 farm path=./subspace-farm,size=2GB --reward-address st7EWm3Y7KBwwX5X7Udz574k5A2d4ybpPfFqJN5Bv1Z2bnnh7 --node-rpc-url ws://127.0.0.1:9944
2024-06-11T12:07:12.575101Z  INFO subspace_farmer::commands::farm: Connecting to node RPC url=ws://127.0.0.1:9944
2024-06-11T12:07:12.575864Z  INFO subspace_farmer::node_client::node_rpc_client: Downloading all segment headers from node...
2024-06-11T12:07:12.576148Z  INFO subspace_farmer::node_client::node_rpc_client: Downloaded all segment headers from node successfully
2024-06-11T12:07:12.577507Z  INFO subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=false peer_id=12D3KooWJdT4KUKhgVKd96KEVYMf5gwMhmFhujczxnMYNcRtHp2q protocol_version=/subspace/2/0180586b2cf95c03465a0705f54907c52f99f3e4aec786cca6f8c6a9a3f4146f
2024-06-11T12:07:12.577796Z  INFO libp2p_swarm: local_peer_id=12D3KooWJdT4KUKhgVKd96KEVYMf5gwMhmFhujczxnMYNcRtHp2q
2024-06-11T12:07:12.903502Z  INFO subspace_farmer::commands::farm: Preparing plotting thread pools plotting_thread_pool_core_indices=[CpuCoreSet { cores: CpuSet(0-15), .. }] replotting_thread_pool_core_indices=[CpuCoreSet { cores: CpuSet(0-7), .. }]
2024-06-11T12:07:12.905757Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plot_cache: Checking plot cache contents, this can take a while
2024-06-11T12:07:12.906798Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plot_cache: Finished checking plot cache contents
2024-06-11T12:07:12.907290Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm: Benchmarking faster proving method
2024-06-11T12:07:14.212577Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm: Faster proving method found fastest_mode=ConcurrentChunks
2024-06-11T12:07:14.226696Z  INFO {farm_index=0}: subspace_farmer::commands::farm: Farm 0:
2024-06-11T12:07:14.226709Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   ID: 01J03K3X892MPD1BXF5EWM9PE8
2024-06-11T12:07:14.226715Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Genesis hash: 0x0180586b2cf95c03465a0705f54907c52f99f3e4aec786cca6f8c6a9a3f4146f
2024-06-11T12:07:14.226717Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Public key: 0xf49f12bd9d2bacb8b9e3fb8d940d8a2f236c838c5e9b5cbd8ba26a5b0f9ca709
2024-06-11T12:07:14.226723Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Allocated space: 1.9 GiB (2.0 GB)
2024-06-11T12:07:14.226725Z  INFO {farm_index=0}: subspace_farmer::commands::farm:   Directory: ./subspace-farm
2024-06-11T12:07:14.226750Z  INFO subspace_farmer::commands::farm: Collecting already plotted pieces (this will take some time)...
2024-06-11T12:07:14.226758Z  INFO subspace_farmer::commands::farm: Finished collecting already plotted pieces successfully
2024-06-11T12:07:14.226766Z  INFO subspace_farmer::farmer_cache: Initializing piece cache
2024-06-11T12:07:14.226862Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plotting: Subscribing to archived segments
2024-06-11T12:07:14.226883Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::farming: Subscribing to slot info notifications
2024-06-11T12:07:14.226899Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Subscribing to reward signing notifications
2024-06-11T12:07:14.226910Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip4/127.0.0.1/tcp/30533/p2p/12D3KooWJdT4KUKhgVKd96KEVYMf5gwMhmFhujczxnMYNcRtHp2q
2024-06-11T12:07:14.227082Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip6/::1/tcp/30533/p2p/12D3KooWJdT4KUKhgVKd96KEVYMf5gwMhmFhujczxnMYNcRtHp2q
2024-06-11T12:07:14.227089Z  INFO subspace_farmer::commands::shared::network: DSN listening on /ip4/192.168.0.101/tcp/30533/p2p/12D3KooWJdT4KUKhgVKd96KEVYMf5gwMhmFhujczxnMYNcRtHp2q
2024-06-11T12:07:14.233021Z  INFO subspace_farmer::farmer_cache: Synchronizing piece cache
2024-06-11T12:07:14.233567Z  INFO {farm_index=0}:{sector_index=0}: subspace_farmer::single_disk_farm::plotting: Plotting sector (0.00% complete)
2024-06-11T12:07:19.905191Z  INFO subspace_farmer::farmer_cache: Piece cache sync 39.06% complete
2024-06-11T12:07:20.531555Z  INFO subspace_farmer::farmer_cache: Piece cache sync 78.12% complete
2024-06-11T12:07:20.855712Z  INFO subspace_farmer::farmer_cache: Finished piece cache synchronization
2024-06-11T12:12:21.758865Z  INFO {farm_index=0}: subspace_farmer::single_disk_farm::plotting: Initial plotting complete
2024-06-11T12:12:31.554264Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x7b197524496746fc1b7381672cbf14ddf1238a2efbad2ae58d3b0c5b4c8348ae
2024-06-11T12:12:39.983906Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x446d8829324a62f5595474b2ed18b7efdea41ea05c59938013c055956f593a6e
2024-06-11T12:12:41.406388Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xf2ef024b4754ac511a183ef5f0760fc02535cb1e7ca42db572f755afc561bcf7
2024-06-11T12:12:42.133649Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x888c38d8d3256660c8f27cad7942e1e6ab72d0b56592eb9c20af1efe4cb5de5c
2024-06-11T12:12:44.299625Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xeee855dbebb5a9da48b27e39c6b2e4361bc8a2fcbf7d19663b9db81c5797cf62
2024-06-11T12:12:45.013803Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x1bd5bcb548734e9c1e872d76e8c2d9b0402204eed25b9dd37588107cc79b104e
2024-06-11T12:12:50.046454Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x52beb450f65b80fb5d1ad0681d98e076389ca2a72510e3580fb1248e227f43f0
2024-06-11T12:12:53.650819Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0x32cb9e8daa190394d9b05099433385e914808d93ce05363c29c43e020731ec78
2024-06-11T12:12:56.529890Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xac0463c39e5a8e109738cad155f65fd2116252966419b61497fc8a372b73da35
2024-06-11T12:13:06.197136Z  INFO {farm_index=0}: subspace_farmer::reward_signing: Successfully signed reward hash 0xb8e739aab5ff6e5adae16b962bcff9e73d1156bdb0201efce7570c3dfe11f48c
```

Now, the block starts producing.

> NOTE: In a substrate-node-template, the blocks are produced automatically based on the consensus algorithm. Here, in subspace, it is driven by farming i.e. your space pledged. More the farmers, merrier it is for Subspace blockchain in terms of decentralization.

> NOTE: Until the farmer node's initial plotting is complete, the subspace node will not produce blocks. In the subspace node, the 2 flags allow farmer to do `reward_signing`: `--farmer` and `--timekeeper`.

### 5. DONE! 🎉

Now, you can send a pallet tx to your subspace consensus chain using some CLI tool like `subxt` or script.

Also, you can test the domain-1 i.e. Nova (EVM-based) chain by sending txs using CLI tool like `foundry` or script (Solidity, TS, Rust).

## Explorer

In order to find an EVM tx (sent to Nova EVM chain or domain-1), you just need to make the standard way of using `cast`/`forge`. And then when you receive a tx hash. Just get some details about the tx using `cast`:

```sh
❯ cast tx 0xc42b04d565ad5683c59a5b8ba6c1567485b6a8d913c065157f000cdb24ab517f --rpc-url $NOVA_RPC_URL

blockHash            0xd9ae7b107f24942ef92c310c648f2031eb2c35e33316513785e41db9a24afb61
blockNumber          5576
from                 0xf24FF3a9CF04c71Dbc94D0b566f7A27B94566cac
gas                  125000
gasPrice             500000000
hash                 0xc42b04d565ad5683c59a5b8ba6c1567485b6a8d913c065157f000cdb24ab517f
input                0xaafea3120000000000000000000000000000000000000000000000000000000000009ce100000000000000000000000071d5a92a9056ab2ee81811af045439e059dd6fbc
nonce                62
r                    0x6d3dec4a4300183e7d8a46cc7b8b978fd3756049ff602fd3924e7d62f252312c
s                    0x5a13810988d2852d8959250dd0cca228a39c8a4fc2d8ef45107a9d2ec0586408
to                   0xb91C2eeaA0c475115069a6ED4bc601337a22788E
transactionIndex     11
v                    980036
value                0
creates              null
```

And then go to Nova explorer via PolkadotJS.

And then search block 5576. After that look for tx at index 11. And then expand `ethereum.Executed` to know the details of the tx.

![](assets/nova_polkadotjs_explorer_tx_details.png)

Congrats! 🎉 You have done it.
