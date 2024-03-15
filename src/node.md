# Node

## Overview

This chapter contains code snippets and functions that can be used to build a Subspace node.

## Build

To build a subspace node binary, do this:

```sh
cargo r -r --bin subspace-node
```

## Run

To run a node, do this:

```sh
# Replace YOUR_NODE_PATH and YOUR_NODE_NAME
./target/release/subspace-node run --chain gemini-3h --base-path YOUR_NODE_PATH --blocks-pruning 256 --state-pruning archive-canonical --farmer --name YOUR_NODE_NAME 
```

> Don't panic, if there is Error shown when connecting to DNS.
> The flag `--validator` in a substrate-node-template cli is changed to `--farmer` here.

<details><summary>Details</summary>

```sh
$ ./target/release/subspace-node run \                                                                                           ⏎
  --chain gemini-3h \
  --base-path ~/subspace-node/alice \
  --farmer \
  --name alice           
2024-03-15T12:58:52.630128Z  INFO subspace_node::commands::run: Subspace
2024-03-15T12:58:52.630226Z  INFO subspace_node::commands::run: ✌️  version 0.1.0-df8d33b65ff
2024-03-15T12:58:52.630239Z  INFO subspace_node::commands::run: ❤️  by Subspace Labs <https://subspace.network>
2024-03-15T12:58:52.630259Z  INFO subspace_node::commands::run: 📋 Chain specification: Subspace Gemini 3h
2024-03-15T12:58:52.630265Z  INFO subspace_node::commands::run: 🏷  Node name: alice
2024-03-15T12:58:52.630271Z  INFO subspace_node::commands::run: 💾 Node path: /Users/abhi3700/subspace-node/alice
2024-03-15T12:58:53.881092Z  INFO Consensus: sc_service::client::client: 🔨 Initializing Genesis block/state (state: 0x4b08…e8c9, header-hash: 0x0c12…1c34)    
2024-03-15T12:58:55.233549Z  INFO Consensus: subspace_networking::constructor: DSN instance configured. allow_non_global_addresses_in_dht=false peer_id=12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd protocol_version=/subspace/2/0c121c75f4ef450f40619e1fca9d1e8e7fbabc42c895bc4790801e85d5a91c34
2024-03-15T12:58:55.250615Z  INFO Consensus: libp2p_swarm: local_peer_id=12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.254734Z  INFO Consensus: subspace_service: Subspace networking initialized: Node ID is 12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.260174Z  INFO Consensus: subspace_service: DSN listening on /ip4/127.0.0.1/udp/30433/quic-v1/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.261994Z  INFO Consensus: block_relay: relay::consensus block server: starting
2024-03-15T12:58:55.264466Z  INFO Consensus: subspace_service: DSN listening on /ip6/::1/udp/30433/quic-v1/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.264597Z  INFO Consensus: subspace_service: DSN listening on /ip4/192.168.0.100/udp/30433/quic-v1/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.264749Z  INFO Consensus: subspace_service: DSN listening on /ip4/127.0.0.1/tcp/30433/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.264939Z  INFO Consensus: subspace_service: DSN listening on /ip6/::1/tcp/30433/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.265029Z  INFO Consensus: subspace_service: DSN listening on /ip4/192.168.0.100/tcp/30433/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd
2024-03-15T12:58:55.269635Z  INFO Consensus: sub-libp2p: 🏷  Local node identity is: 12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd    
2024-03-15T12:58:55.281480Z  INFO Consensus: sc_consensus_subspace::archiver: Starting archiving from genesis
2024-03-15T12:58:55.281611Z  INFO Consensus: sc_consensus_subspace::archiver: Archiving already produced blocks 0..=0
2024-03-15T12:59:10.394272Z  INFO Consensus: subspace: 🧑‍🌾 Starting Subspace Authorship worker
2024-03-15T12:59:10.395164Z  INFO Consensus: sc_sysinfo: 💻 Operating system: macos    
2024-03-15T12:59:10.395181Z  INFO Consensus: sc_sysinfo: 💻 CPU architecture: aarch64    
2024-03-15T12:59:10.395728Z  INFO Consensus: sc_service::builder: 📦 Highest known block at #0    
2024-03-15T12:59:10.403125Z  INFO Consensus: sc_rpc_server: Running JSON-RPC server: addr=127.0.0.1:9944, allowed origins=["http://localhost:*", "http://127.0.0.1:*", "https://localhost:*", "https://127.0.0.1:*", "https://polkadot.js.org"]    
2024-03-15T12:59:10.653126Z  INFO connection{remote_addr=127.0.0.1:50732 conn_id=0}: jsonrpsee_server::server: Accepting new connection 1/100
2024-03-15T12:59:11.393128Z  INFO Consensus: subspace_service::sync_from_dsn: Received notification to sync from DSN reason=WentOnlineSubstrate
2024-03-15T12:59:11.472245Z  INFO Consensus: sub-libp2p: 🔍 Discovered new external address for our node: /ip4/49.37.33.103/tcp/30333/p2p/12D3KooWC9DWpHah8U1S1omqYefmVup2TFLxiX2c9EJfVZW1dVKd    
2024-03-15T12:59:15.429418Z  INFO Consensus: substrate: ⚙️  Syncing, target=#643359 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 6.4kiB/s ⬆ 1.4kiB/s    
2024-03-15T12:59:20.431456Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643360 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 5.9kiB/s ⬆ 74 B/s    
2024-03-15T12:59:25.433975Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643361 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 5.4kiB/s ⬆ 36 B/s    
2024-03-15T12:59:30.435151Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643361 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 5.1kiB/s ⬆ 0.4kiB/s    
2024-03-15T12:59:30.436724Z  WARN Consensus: telemetry: ❌ Error while dialing /dns/telemetry.subspace.network/tcp/443/x-parity-wss/%2Fsubmit%2F: Custom { kind: Other, error: Timeout }    
2024-03-15T12:59:35.435507Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643361 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 4.7kiB/s ⬆ 21 B/s    
2024-03-15T12:59:40.439349Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643362 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 13.9kiB/s ⬆ 4.1kiB/s    
2024-03-15T12:59:45.439883Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643362 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 16.1kiB/s ⬆ 1.4kiB/s    
2024-03-15T12:59:50.440773Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643366 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 11.1kiB/s ⬆ 1.7kiB/s    
2024-03-15T12:59:55.441357Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643366 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 10.4kiB/s ⬆ 1.7kiB/s    
2024-03-15T13:00:00.441777Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643367 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 5.8kiB/s ⬆ 0.8kiB/s    
2024-03-15T13:00:05.442238Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643368 (3 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 14.8kiB/s ⬆ 1.5kiB/s    
2024-03-15T13:00:10.443021Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643368 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 17.6kiB/s ⬆ 1.7kiB/s    
2024-03-15T13:00:10.443523Z  WARN Consensus: telemetry: ❌ Error while dialing /dns/telemetry.subspace.network/tcp/443/x-parity-wss/%2Fsubmit%2F: Custom { kind: Other, error: Timeout }    
2024-03-15T13:00:15.445954Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643369 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 13.3kiB/s ⬆ 0.7kiB/s    
2024-03-15T13:00:20.446970Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643370 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 12.4kiB/s ⬆ 1.0kiB/s    
2024-03-15T13:00:25.453759Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643372 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 12.4kiB/s ⬆ 0.9kiB/s    
2024-03-15T13:00:30.454210Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643373 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 12.4kiB/s ⬆ 2.4kiB/s    
2024-03-15T13:00:35.459006Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643374 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 13.3kiB/s ⬆ 1.6kiB/s    
2024-03-15T13:00:40.468017Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643374 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 18.9kiB/s ⬆ 6.0kiB/s    
2024-03-15T13:00:45.468435Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643374 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 10.2kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:00:50.483765Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643375 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 11.1kiB/s ⬆ 0.4kiB/s    
2024-03-15T13:00:50.484125Z  WARN Consensus: telemetry: ❌ Error while dialing /dns/telemetry.subspace.network/tcp/443/x-parity-wss/%2Fsubmit%2F: Custom { kind: Other, error: Timeout }    
2024-03-15T13:00:55.485754Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643376 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 10.1kiB/s ⬆ 0.8kiB/s    
2024-03-15T13:01:00.490096Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643377 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 16.8kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:01:05.497731Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643377 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 11.8kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:01:10.498301Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643377 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 8.4kiB/s ⬆ 1.0kiB/s    
2024-03-15T13:01:15.501357Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643380 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 9.9kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:01:20.502322Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643380 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 9.5kiB/s ⬆ 0.9kiB/s    
2024-03-15T13:01:25.505732Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 16.2kiB/s ⬆ 2.2kiB/s    
2024-03-15T13:01:30.506511Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 15.3kiB/s ⬆ 3.4kiB/s    
2024-03-15T13:01:35.506949Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 16.8kiB/s ⬆ 3.9kiB/s    
2024-03-15T13:01:40.507863Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 9.7kiB/s ⬆ 1.2kiB/s    
2024-03-15T13:01:45.508176Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 15.7kiB/s ⬆ 0.8kiB/s    
2024-03-15T13:01:50.513373Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (5 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 12.1kiB/s ⬆ 0.7kiB/s    
2024-03-15T13:01:55.514332Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643382 (2 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 302.4kiB/s ⬆ 2.9kiB/s    
2024-03-15T13:02:00.516728Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643381 (1 peers), best: #0 (0x0c12…1c34), finalized #0 (0x0c12…1c34), ⬇ 813.3kiB/s ⬆ 2.1kiB/s    
2024-03-15T13:02:05.519233Z  INFO Consensus: substrate: ⚙️  Syncing 32.7 bps, target=#643381 (1 peers), best: #164 (0xf143…279c), finalized #0 (0x0c12…1c34), ⬇ 777.2kiB/s ⬆ 1.2kiB/s    
2024-03-15T13:02:10.519911Z  INFO Consensus: substrate: ⚙️  Syncing 18.4 bps, target=#643386 (2 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 850.4kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:02:15.520371Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643388 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 821.6kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:02:20.522099Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643382 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 856.8kiB/s ⬆ 1.6kiB/s    
2024-03-15T13:02:25.522786Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643382 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 781.8kiB/s ⬆ 2.8kiB/s    
2024-03-15T13:02:30.525284Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643389 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 796.7kiB/s ⬆ 3.0kiB/s    
2024-03-15T13:02:35.532801Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643389 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 828.4kiB/s ⬆ 1.6kiB/s    
2024-03-15T13:02:36.997024Z  INFO connection{remote_addr=127.0.0.1:59414 conn_id=1}: jsonrpsee_server::server: Accepting new connection 1/100
2024-03-15T13:02:40.535904Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643389 (3 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 826.0kiB/s ⬆ 1.8kiB/s    
2024-03-15T13:02:43.244467Z  INFO connection{remote_addr=127.0.0.1:59999 conn_id=2}: jsonrpsee_server::server: Accepting new connection 1/100
2024-03-15T13:02:45.538576Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643389 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 956.7kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:02:50.539712Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643391 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 1.1MiB/s ⬆ 1.2kiB/s    
2024-03-15T13:02:55.545209Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643392 (1 peers), best: #256 (0x3461…0eba), finalized #0 (0x0c12…1c34), ⬇ 1013.3kiB/s ⬆ 1.3kiB/s    
2024-03-15T13:03:00.550520Z  INFO Consensus: substrate: ⚙️  Syncing 23.9 bps, target=#643393 (1 peers), best: #376 (0x7cd8…5ab1), finalized #0 (0x0c12…1c34), ⬇ 949.6kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:03:05.552507Z  INFO Consensus: substrate: ⚙️  Syncing 27.1 bps, target=#643393 (1 peers), best: #512 (0xd220…8266), finalized #0 (0x0c12…1c34), ⬇ 852.6kiB/s ⬆ 0.7kiB/s    
2024-03-15T13:03:10.556612Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643395 (1 peers), best: #512 (0xd220…8266), finalized #0 (0x0c12…1c34), ⬇ 810.0kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:03:15.561883Z  INFO Consensus: substrate: ⚙️  Syncing 12.7 bps, target=#643395 (2 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 851.5kiB/s ⬆ 1.3kiB/s    
2024-03-15T13:03:20.567211Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643395 (2 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 962.4kiB/s ⬆ 2.6kiB/s    
2024-03-15T13:03:25.572115Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643395 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 1.1MiB/s ⬆ 2.4kiB/s    
2024-03-15T13:03:30.575924Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643398 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 851.8kiB/s ⬆ 2.5kiB/s    
2024-03-15T13:03:35.577190Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643399 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 859.0kiB/s ⬆ 1.3kiB/s    
2024-03-15T13:03:40.581185Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643400 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 816.4kiB/s ⬆ 1.6kiB/s    
2024-03-15T13:03:45.581547Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643401 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 788.8kiB/s ⬆ 1.3kiB/s    
2024-03-15T13:03:50.583358Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643403 (1 peers), best: #576 (0xd0e3…a727), finalized #0 (0x0c12…1c34), ⬇ 760.0kiB/s ⬆ 0.9kiB/s    
2024-03-15T13:03:55.583704Z  INFO Consensus: substrate: ⚙️  Syncing 11.8 bps, target=#643404 (2 peers), best: #635 (0x9ff0…767d), finalized #0 (0x0c12…1c34), ⬇ 740.3kiB/s ⬆ 1.6kiB/s    
^[2024-03-15T13:04:00.586081Z  INFO Consensus: substrate: ⚙️  Syncing  0.9 bps, target=#643404 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 776.8kiB/s ⬆ 1.0kiB/s    
2024-03-15T13:04:05.591517Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643404 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 796.2kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:04:10.595130Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643404 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 815.6kiB/s ⬆ 1.5kiB/s    
2024-03-15T13:04:15.600408Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643406 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 798.3kiB/s ⬆ 2.7kiB/s    
2024-03-15T13:04:18.250459Z  INFO connection{remote_addr=127.0.0.1:53125 conn_id=3}: jsonrpsee_server::server: Accepting new connection 1/100
2024-03-15T13:04:20.605790Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643405 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 815.7kiB/s ⬆ 2.1kiB/s    
2024-03-15T13:04:25.606110Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643406 (2 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 857.7kiB/ ⬆ 2.7kiB/s    
2024-03-15T13:04:30.608167Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643407 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 777.6kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:04:35.613519Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643407 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 777.4kiB/s ⬆ 1.1kiB/s    
2024-03-15T13:04:40.618309Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643408 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 782.9kiB/s ⬆ 1.4kiB/s    
2024-03-15T13:04:45.618697Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643409 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 729.1kiB/s ⬆ 1.0kiB/s    
2024-03-15T13:04:50.621701Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643410 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 564.0kiB/s ⬆ 0.9kiB/s    
2024-03-15T13:04:55.627145Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643410 (2 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 533.8kiB/s ⬆ 1.5kiB/s    
2024-03-15T13:05:00.629073Z  INFO Consensus: substrate: ⚙️  Syncing  0.0 bps, target=#643411 (1 peers), best: #640 (0x5a2c…0938), finalized #0 (0x0c12…1c34), ⬇ 658.7kiB/s ⬆ 1.2kiB/s    
```

</details>

---

To wipe the node data using CLI:

```sh
./target/release/subspace-node wipe ~/subspace-node/alice
2024-03-15T13:22:25.186058Z  INFO subspace_node::commands::wipe: Removing /Users/abhi3700/subspace-node/alice/db
2024-03-15T13:22:25.389770Z  INFO subspace_node::commands::wipe: Removing /Users/abhi3700/subspace-node/alice/network
2024-03-15T13:22:25.390382Z  INFO subspace_node::commands::wipe: Done
```

> Replaced `purge-chain --base-path` in `substrate-node-template` with `wipe` subcommand here. Actually, there is a config file stored somewhere which keeps track of the chain name. So, no need to explicitly provide that unlike in `substrate-node-template`, where it is required like `./substrate-node-template purge-chain --base-path ~/subspace-node/alice --chain gemini-3h -y`.

## Recipes

### What are the local dependencies for creating a subspace node?

Here are the crates that are used to create a subspace node:

```toml
sdk-substrate
sdk-node
```

### How a subspace node type is defined?

```rust
use subspace_proof_of_space::chia::ChiaTable;

/// Subspace farmer type
pub type Farmer = sdk_farmer::Farmer<ChiaTable>;

/// Subspace primary node
pub type Node = sdk_node::Node<Farmer>;
```

### How to create a simple Subspace node?

```rust
//! Source code at file: https://github.com/subspace/subspace-sdk/blob/main/examples/simple.rs

// import the required crates
use subspace_sdk::Node;
use sdk_node::PotConfiguration;

let node = subspace_sdk::Node::builder()
    .force_authoring(true)
    .role(subspace_sdk::node::Role::Authority)
    // Starting a new chain
    .build(
        "node",
        subspace_sdk::chain_spec::dev_config(),
        PotConfiguration { is_pot_enabled: false, is_node_time_keeper: true },
    )
    .await
    .unwrap();
```

### How to create an advanced Subspace node with some network option to listen for peers' addresses?

```rust
//! Source code at file: https://github.com/subspace/subspace-sdk/blob/main/examples/sync.rs

// import the required crates
use subspace_sdk::Node;
use subspace_sdk::node::NetworkBuilder;
use sdk_node::PotConfiguration;

// create a node
let node = Node::builder()
    .network(
        // create a network builder which is defined as struct - `Network` to be called as `NetworkBuilder`
        NetworkBuilder::new()
            .listen_addresses(vec!["/ip4/127.0.0.1/tcp/0".parse().unwrap()])
            .force_synced(true),
    )
    .force_authoring(true)
    .role(subspace_sdk::node::Role::Authority)
    .build(
        // this `node` is of PathBuf type
        node,
        // `chain_spec` is defined in the `chain_spec.rs` file which needs to be read.
        chain_spec,
        PotConfiguration { is_pot_enabled: false, is_node_time_keeper: true },
    )
    .await?;
```

### How to stop a node to author blocks after running few blocks?

```rust
// define a node
// === code from `examples/simple.rs` ===

// stop authoring blocks after running 10 blocks
node.subscribe_new_heads()
    .await
    .unwrap()
    // Wait 10 blocks and exit
    .take(10)
    .for_each(|header| async move { tracing::info!(?header, "New block!") })
    .await;
```

Here, `take(10)` method will stop authoring blocks after running 10 blocks.

In order to view fresh block production, you have to remove the `parity_db` folder, else it will stop producing blocks after 10 blocks like `0` -> `9` and then `9` -> `18` and `18` -> `27` and so on.

> Please note here that the block which the previous iteration ended at, the same block number the next iteration will start from. E.g. Like in this case, run-1 ended at `9` block, run-2 will start from `9` block and end at `18` block and so on. So, the total blocks produced is 10 in each iteration.

```sh
rm -rf /path/to/parity_db
```

### How to set a chain spec for a node?
