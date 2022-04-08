# cb-sol-cli Documentation

This CLI supports on-chain interactions with components of ChainBridge.

## Installation 

Installation requires the ABI files from the contracts which will be fetched and built from the chainbridge-solidity repo.
```
$ make install
```

## Usage 

The root command (`cb-sol-cli`) has some options:
```
--url <value>                 URL to connect to
--gasLimit <value>            Gas limit for transactions 
--gasPrice <value>            Gas price for transactions 
--networkId <value>	      Network id
```
\
The keypair used for interactions can be configured with:
```
--privateKey <value>           Private key to use
```
or
```
--jsonWallet <path>           Encrypted JSON wallet
--jsonWalletPassword <value>  Password for encrypted JSON wallet
```

There are multiple subcommands provided:

- [`deploy`](docs/deploy.md): Deploys contracts via RPC
- [`bridge`](docs/bridge.md): Interactions with the bridge contract such as registering resource IDs and handler addresses
- [`admin`](docs/admin.md): Interactions with the bridge contract for administering relayer set, relayer threshold, fees and more.
- [`erc20`](docs/erc20.md): Interactions with ERC20 contracts and handlers
- [`erc721`](docs/erc721.md): Interactions with ERC721 contracts and handler


## Deployment

**Note: The following steps should be further refine.**
The current stable build is found in `feature/v2` branch, where the `cli.sh` is located in `cb-sol-cli` folder.

### Setting up the environment variables
Go to `Gdrive -> Alt Dev Docs -> bridge -> ChainBridge 使用手册`, copy the bash script into a file called `env.sh` and place it inside `cb-sol-cli` folder.
This will preset all the hardcoded keys and generated APIs.

TODO: To generalise this portion

### Contract deployment
To deploy, `./cli.sh <ETH network> deploy`. Upon completion of deployment, update `env.sh` with the new values of the deployed contracts i.e ERC-20, ERC-721 contracts and the related handler contracts.
- BRIDGE_ADDR_<ETH network>
- ERC20_HANDLER_<ETH network>
- ERC20_ADDR_ALT1_<ETH network>
- ERC721_ADDR_NFT1_<ETH network>
- ERC721_HANDLER_<ETH network>

TODO: Seperate the deploy steps for bridge and token contracts. Make the process more generic.

### Initialise the contracts
To initialise the contracts, `./cli.sh <ETH network> init`
Upon completion of deployment, update `env.sh` with the new values of the resourceID ERC-20/ERC-721 contracts.
- RESOURCE_ID_ALT1
- RESOURCE_ID_NFT1

Note: ResourceID is currently a random generated 32-bytes string that assocate with one particular token on the bridge.
