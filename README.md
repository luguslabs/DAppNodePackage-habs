# DAppNodePackage-archipel
Archipel package for DAppNode 


### Configuration parameters

| Variable | Description | Values |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| `ARCHIPEL_NODE_ALIAS` | Node name for the Archipel Substrate node within the federation. | String. Example`Archipel-"yourFederationName"-"Node Name here`|
| `ARCHIPEL_KEY_SEED` | 12 words mnemonic. Can be generated with [Subkey](https://substrate.dev/docs/en/ecosystem/subkey). Use for Archipel Substrate node. Will be used for consensus authority and transactions propagation in the Archipel Chain. | mnemonic |
| `ARCHIPEL_CHAIN_ADDITIONAL_PARAMS` | Parameters supported by substrate node. At least, you must valorize bootnodes. Tu valorize bootnodes you must start nodes first and then rebbot all your 3 nodes in the federation with bootnode list valorized thank to local node id find in logs. | --bootnodes /ip4/$NODE1_IP/tcp/30333/p2p/$NODE1_LOCAL_ID --bootnodes /ip4/$NODE2_IP/tcp/30333/p2p/$NODE2_LOCAL_ID --bootnodes /ip4/$NODE3_IP/tcp/30333/p2p/$NODE3_LOCAL_ID"
| `ARCHIPEL_AUTHORITIES_SR25519_LIST` | Genesis Specification file for Archipel chain must the list of Authorities Public Keys in SR25519 format  | <SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>
| `ARCHIPEL_AUTHORITIES_ED25519_LIST` | Genesis Specification file for Archipel chain must the list of Authorities Public Keys in ED25519 format  | <ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>
| `POLKADOT_NAME` | Node name for the polkadot node. Will be visible in [Polkadot telemetry](https://telemetry.polkadot.io/). This Node Name will a a -passive or -active suffix according to the current mode. | String. Example`Archipel-"yourFederationName"-"Node Name here` |
| `POLKADOT_PREFIX` | This prefix is used to mount the docker volume for blockchain state on the server. | String |
| `SERVICE` | external service you want to launch. Only support polkadot at the moment | polkadot |
| `POLKADOT_IMAGE` | Polkadot docker image version to use. |  parity/polkadot:latest |
| `POLKADOT_KEY_GRAN` | Polkadot Sessions keys needed to operate as validator. Gran keyType, Granpa ed25519. Use for consensus [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_BABE` | Polkadot Sessions keys needed to operate as validator. Babe keyType, Babe sr25519. Use for consensus/block production [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_IMON` | Polkadot Sessions keys needed to operate as validator. IMON keyType, IamOnline key. Use for heartbeat/block production [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_PARA` | Polkadot Sessions keys needed to operate as validator. PARA keyType. sr25519. Use for parachain production [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_AUDI` | Polkadot Sessions keys needed to operate as validator. AUDI keyType. sr25519. Use for  [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
