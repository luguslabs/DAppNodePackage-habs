
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

| Variable | Description | Values |
|----------|-------------|--------|
| `ARCHIPEL_NODE_ALIAS` | Node name for the Archipel Substrate node within the federation. <br>Example<br> `Archipel-yourFederationName-NodeNameHere` | String |
| `ARCHIPEL_KEY_SEED` | 12 words mnemonic. <br> Can be generated with [Subkey](https://substrate.dev/docs/en/ecosystem/subkey). <br>Use for Archipel Substrate node. <br>Will be used for consensus authority and transactions propagation in the Archipel Chain. | mnemonic |
| `ARCHIPEL_CHAIN_ADDITIONAL_PARAMS` | Parameters supported by substrate node.<br> At least, you must valorize bootnodes. To valorize bootnodes you must start nodes first and then rebbot all your 3 nodes in the federation with bootnode list valorized thank to local node id find in logs. <br>Example :<br> `--bootnodes /ip4/$NODE1_IP/tcp/30333/p2p/$NODE1_LOCAL_ID --bootnodes /ip4/$NODE2_IP/tcp/30333/p2p/$NODE2_LOCAL_ID --bootnodes /ip4/$NODE3_IP/tcp/30333/p2p/$NODE3_LOCAL_ID` | String
| `ARCHIPEL_AUTHORITIES_SR25519_LIST` | Valorize the Genesis [Spec file](https://github.com/luguslabs/archipel/blob/master/deployer/test/chain/customSpec.json) for Archipel chain with the list of Authorities Public Keys in SR25519 format separated by \",\" char.<br> `<SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>`|  Public Key, Public Key, Public Key
| `ARCHIPEL_AUTHORITIES_ED25519_LIST` | Valorize the Genesis [Spec file](https://github.com/luguslabs/archipel/blob/master/deployer/test/chain/customSpec.json) for Archipel chain with the list of Authorities Public Keys in ED25519 format separated by \",\" char.<br>`<ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>`| Public Key, Public Key, Public Key
| `SERVICE` | External service you want to launch. Only support `polkadot` at the moment. | polkadot |
| `POLKADOT_NAME` | Node name for the polkadot node. Will be visible in [Polkadot telemetry](https://telemetry.polkadot.io/). This Node Name will a a -passive or -active suffix according to the current mode. <br>Example<br>`Archipel-yourFederationName-NodeNameHere` | String |
| `POLKADOT_IMAGE` | Polkadot docker image version to use. |  parity/polkadot:latest |
| `POLKADOT_PREFIX` | This prefix is used to mount the docker volume for blockchain state on the server. | String |
| `POLKADOT_KEY_GRAN` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator. <br>Gran keyType, Granpa ed25519.<br> Use for consensus.<br> [More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_BABE` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> Babe keyType, Babe sr25519. <br>Use for consensus/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_IMON` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> IMON keyType, IamOnline key.<br> Use for heartbeat/block production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_PARA` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> PARA keyType. sr25519. <br>Use for parachain production. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |
| `POLKADOT_KEY_AUDI` |12 words mnemonic. <br> Polkadot Sessions keys needed to operate as validator.<br> AUDI keyType. sr25519.<br> Use for Audit. <br>[More details for sessions keys](https://github.com/luguslabs/archipel/tree/master/orchestrator#polkadot-sessions-keys-explained)| mnemonic |


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

