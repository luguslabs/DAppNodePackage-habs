# DAppNodePackage-archipel
Archipel package for DAppNode 


### Configuration parameters

| Variable | Description | Values |
|----------|-------------|--------|
| `ARCHIPEL_NODE_ALIAS` | Node name for the Archipel Substrate node within the federation. <br>Example<br> `Archipel-yourFederationName-NodeNameHere` | String |
| `ARCHIPEL_KEY_SEED` | 12 words mnemonic. <br> Can be generated with [Subkey](https://substrate.dev/docs/en/ecosystem/subkey). <br>Use for Archipel Substrate node. <br>Will be used for consensus authority and transactions propagation in the Archipel Chain. | mnemonic |
| `ARCHIPEL_CHAIN_ADDITIONAL_PARAMS` | Parameters supported by substrate node.<br> At least, you must valorize bootnodes. To valorize bootnodes you must start nodes first and then rebbot all your 3 nodes in the federation with bootnode list valorized thank to local node id find in logs. <br>Example :<br> `--bootnodes /ip4/$NODE1_IP/tcp/30333/p2p/$NODE1_LOCAL_ID --bootnodes /ip4/$NODE2_IP/tcp/30333/p2p/$NODE2_LOCAL_ID --bootnodes /ip4/$NODE3_IP/tcp/30333/p2p/$NODE3_LOCAL_ID` | String
| `ARCHIPEL_AUTHORITIES_SR25519_LIST` | Genesis Specification file for Archipel chain must the list of Authorities Public Keys in SR25519 format. <br> `<SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>`|  Public Key, Public Key, Public Key
| `ARCHIPEL_AUTHORITIES_ED25519_LIST` | Genesis Specification file for Archipel chain must the list of Authorities Public Keys in ED25519 format.<br>`<ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>`| Public Key, Public Key, Public Key
| `POLKADOT_NAME` | Node name for the polkadot node. Will be visible in [Polkadot telemetry](https://telemetry.polkadot.io/). This Node Name will a a -passive or -active suffix according to the current mode. <br>Example<br>`Archipel-yourFederationName-NodeNameHere` | String |
| `POLKADOT_PREFIX` | This prefix is used to mount the docker volume for blockchain state on the server. | String |
| `SERVICE` | External service you want to launch. Only support polkadot at the moment | polkadot |
| `POLKADOT_IMAGE` | Polkadot docker image version to use. |  parity/polkadot:latest |
| `POLKADOT_KEY_GRAN` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator. <br>Gran keyType, Granpa ed25519.<br> Use for consensus.<br> [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_BABE` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> Babe keyType, Babe sr25519. <br>Use for consensus/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_IMON` | 12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> IMON keyType, IamOnline key.<br> Use for heartbeat/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_PARA` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> PARA keyType. sr25519. <br>Use for parachain production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_AUDI` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> AUDI keyType. sr25519.<br> Use for Audit. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
