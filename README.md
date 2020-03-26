
# DAppNode Package Archipel
![stability-wip](https://img.shields.io/badge/stability-work_in_progress-lightgrey.svg)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Website archipel.id](https://img.shields.io/badge/Website-archipel.id-brightgreen.svg)](https://archipel.id/)
[![Documentation Readme](https://img.shields.io/badge/Documentation-Wiki-brightgreen.svg)](https://github.com/luguslabs/archipel)
[![Twitter Follow](https://img.shields.io/twitter/follow/espadrine.svg?style=social&label=Follow)](https://twitter.com/luguslabs)

Dappnode package responsible for providing the Archipel service.

Actually based on version [v0.0.2](https://github.com/luguslabs/archipel/releases/tag/v0.0.2) of [Archipel](https://github.com/luguslabs/archipel)

It is an AragonApp whose repo is deployed at this address: [0x9f85ae5aefe4a3eff39d9a44212aae21dd15079a ](https://etherscan.io/address/0x9f85ae5aefe4a3eff39d9a44212aae21dd15079a) and whose ENS address is: [archipel.public.dappnode.eth](https://etherscan.io/enslookup?q=archipel.public.dappnode.eth])

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

- git

  Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

  Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding current user to docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

  Install [docker-compose](https://docs.docker.com/compose/install)

**Note**: Make sure you can run `git`, `docker ps`, `docker-compose` without any issue and without sudo command.

### Building

```
$ git clone https://github.com/luguslabs/DAppNodePackage-archipel
```

```
$ docker-compose build
or
$ docker build --rm -f build/Dockerfile -t dnp_archipel:dev build
```


### Configuration env parameters needed

### Environment Variables

#### With config file
The ZIP config file can be generate with [archipel CLI](https://github.com/luguslabs/archipel/tree/master/cli#use)
| Variable | Description | Values |
|----------|-------------|--------|
| `CONFIG_FILE` |Try to load configuration from configuration archive or not. | boolean |
| `CONFIG_FILE_PASSWORD` |Configuration archive can be protected by a password. | string |
| `NODE_ID` |Every configuration archive contains configuration of multiple nodes.<br> You must select node number. | integer |

#### Without config file

| Variable | Description | Values |
|----------|-------------|--------|
| `WIREGUARD_PRIVATE_KEY` | Wireguard private key. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | String |
| `WIREGUARD_PEERS_PUB_ADDR` | Wireguard public key. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | String |
| `WIREGUARD_ADDRESS` | Wireguard address in the wireguard private network. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | 10.0.1.n/32 |
| `WIREGUARD_LISTEN_PORT` | Port UDP of the private network. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | 51820 |
| `WIREGUARD_PEERS_ALLOWED_IP` | all peers address in the private network separate by `,`. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | 10.0.1.1/32,10.0.1.2/32,10.0.1.3/32 |
| `WIREGUARD_PEERS_EXTERNAL_ADDR` | all public IP address of peers separate by `,`. More details in [Archipel Wireguard Keys Initialization](https://github.com/luguslabs/archipel/blob/master/doc/wireguard-keys-initialization.md) | PUBLIC_IP_1,PUBLIC_IP_2,PUBLIC_IP_3 |
| `ARCHIPEL_NODE_ALIAS` | Node name for the Archipel Substrate node within the federation. <br>Example<br> `Archipel-yourFederationName-NodeNameHere` | String |
| `ARCHIPEL_LISTEN_PORT` | Archipel Substrate listen port | 30334
| `ARCHIPEL_NODE_KEY_FILE` | Binary node key file name that must be present in container volume /config/ARCHIPEL_NODE_KEY_FILE. Value is used then with Substrate option `--node-key-file`. <br> Note that bin file is generate with [subkey generate-node-key](https://github.com/luguslabs/archipel/blob/master/bootstrap/src/substrate.js#L29) | String |
| `ARCHIPEL_KEY_SEED` |  | mnemonic |
| `ARCHIPEL_RESERVED_PEERS` | valorize `--reserved-nodes` substrate option. Note that archipel substrate is also launch with `--reserved-only` option.<br> Example :<br> `/ip4/WIREGUARD_ADDRESS_1/tcp/ARCHIPEL_LISTEN_PORT/p2p/NODE_PEER_ID_1,/ip4/WIREGUARD_ADDRESS_2/tcp/ARCHIPEL_LISTEN_PORT/p2p/NODE_PEER_ID_2,/ip4/WIREGUARD_ADDRESS_3/tcp/ARCHIPEL_LISTEN_PORT/p2p/NODE_PEER_ID_3` | String
| `ARCHIPEL_AUTHORITIES_SR25519_LIST` | Valorize the Genesis [Spec file](https://github.com/luguslabs/archipel/blob/master/deployer/test/chain/customSpec.json) for Archipel chain with the list of Authorities Public Keys in SR25519 format separated by \",\" char.<br> `<SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>`|  Public Key, Public Key, Public Key
| `ARCHIPEL_AUTHORITIES_ED25519_LIST` | Valorize the Genesis [Spec file](https://github.com/luguslabs/archipel/blob/master/deployer/test/chain/customSpec.json) for Archipel chain with the list of Authorities Public Keys in ED25519 format separated by \",\" char.<br>`<ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>`| Public Key, Public Key, Public Key
| `ARCHIPEL_TELEMETRY_URL` | Optional TELEMETRY_URL for Archipel substrate node. Example : `ws://BACKEND_PUBLIC_IP:8000/submit` | URL or `--no-telemetry` |
| `ARCHIPEL_SUSPEND_SERVICE` | If true the service node is never switch to active and remains passive. | boolean |
| `SERVICE` | External service you want to launch. Only support `polkadot` at the moment. | polkadot |
| `POLKADOT_NAME` | Node name for the polkadot node. Will be visible in [Polkadot telemetry URL](https://telemetry.polkadot.io/). This Node Name will a a -passive or -active suffix according to the current mode. <br>Example<br>`Archipel-yourFederationName-NodeNameHere` | String |
| `POLKADOT_IMAGE` | Polkadot docker image version to use. |  parity/polkadot:latest |
| `POLKADOT_PREFIX` | This prefix is used to mount the docker volume for blockchain state on the server. | String |
| `POLKADOT_KEY_GRAN` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator. <br>Gran keyType, Granpa ed25519.<br> Use for consensus.<br> [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_BABE` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> Babe keyType, Babe sr25519. <br>Use for consensus/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_IMON` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> IMON keyType, IamOnline key.<br> Use for heartbeat/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_PARA` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> PARA keyType. sr25519. <br>Use for parachain production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_AUDI` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> AUDI keyType. sr25519.<br> Use for Audit. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_NODE_KEY_FILE` | Binary node key file name that must be present in container volume `/config/POLKADOT_NODE_KEY_FILE`. <br> Will be then present in polkdaot container in folder `/polkadot/keys/`. <br> Value is used then with Polkadot option `--node-key-file`. <br> Note that bin file is generate with [subkey generate-node-key](https://github.com/luguslabs/archipel/blob/master/bootstrap/src/substrate.js#L29) | String |
| `POLKADOT_RESERVED_NODES` | valorize `--reserved-nodes` substrate option. <br> Note that polkadot is also launch with `--reserved-only` for validator ( active ) mode. <br> Example :<br> `/ip4/WIREGUARD_ADDRESS_1/tcp/30333/p2p/POLKADOT_NODE_PEER_ID_1,/ip4/WIREGUARD_ADDRESS_2/tcp/30333/p2p/POLKADOT_NODE_PEER_ID_2,/ip4/WIREGUARD_ADDRESS_3/tcp/30333/p2p/POLKADOT_NODE_PEER_ID_3` | String
| `POLKADOT_TELEMETRY_URL` | Optional TELEMETRY_URL for Polkadot Node. Example : `ws://BACKEND_PUBLIC_IP:8000/submit` | URL or `--no-telemetry` |
| `POLKADOT_LAUNCH_IN_VPN` | Use wireguard network for Polkadot | true |
| `POLKADOT_SIMULATE_SYNCH` | Use for testing purpuse to not wait Kusama to be synch to test active/passive switches| false 
| `POLKADOT_ADDITIONAL_OPTIONS` | all others polkadot commands can be set in this env varibale separated with a space | --option1 value1 --options2 value2  




## Running

### Start

```
$ docker-compose up -d
```

### Stop

```
$ docker-compose down
```

### Status

```
$ docker-compose ps
```

### Logs

```
$ docker-compose logs -f
```

**Note**:
There is a time drift issue on Docker for Mac, to solve it try running [Fixing Time drift issue on Docker for Mac](https://blog.shameerc.com/2017/03/quick-tip-fixing-time-drift-issue-on-docker-for-mac):

```
$ docker run --rm --privileged alpine hwclock -s
```

## Generating a tar.xz image

[xz](https://tukaani.org/xz/) is required

```
$ docker save dnp_archipel:dev | xz -e9vT0 > dnp_archipel_dev.tar.xz
```

You can download the latest tar.xz version from here [releases](https://github.com/luguslabs/archipel/releases).

### Loading a Docker image

```
$docker load -i dnp_archipel_dev.tar.xz
```

## Contributing

Please read [CONTRIBUTING.md](TBD) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/luguslabs/archipel/tags).

## Authors

- **Vladimir Ostapenco** - _Initial work_ - [vladostp](https://github.com/vladostp)
- **Francois Branciard** - _Initial work_ - [branciard](https://github.com/branciard)

See also the list of [contributors](https://github.com/luguslabs/archipel/contributors) who participated in this project.

## License

This project is licensed under Apache 2 - see the [LICENSE](LICENSE) file for details

## References

[git](https://git-scm.com/)

[docker](https://www.docker.com/)

[docker-compose](https://docs.docker.com/compose/)

[DappNode](https://www.dappnode.io/)


## Acknowledgements
<p align="center">
  <img src=./web3_foundation_grants_badge.svg width = 400>
</p>

The bootstrap development of Archipel is financed by [WEB3 Foundation](https://web3.foundation/)'s grant program [Wave4](https://medium.com/web3foundation/wrap-up-for-winter-with-our-wave-four-grant-recipients-52c27b831a6e). Thanks a lot for support.

