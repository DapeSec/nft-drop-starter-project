# buildspace Solana NFT Drop Project
### Welcome 👋
To get started with this course, clone this repo and follow these commands:

1. cd into the `app` folder
2. Run `npm install` at the root of your directory
3. Run `npm run start` to start the project
4. Start coding!

### What is the .vscode Folder?
If you use VSCode to build your app, we included a list of suggested extensions that will help you build this project! Once you open this project in VSCode, you will see a popup asking if you want to download the recommended extensions :).

# Solana NFT Drop

## Summary

Deploy NFT's on Solana blockcahin using Metaplex and Candy Machine.

## Prereqs

vscode
Solana CLI
Metaplex 4.7.0
Metaplex CLI 0.0.2
git - version 2.31.1 (or higher!)
node - v14.17.0 (or higher, below v17 -- we found that node v16 works best)
yarn - 1.22.11 (or higher!)
ts-node - v10.2.1 (or higher!)

## Install Metaplex CLI

Open Terminal.

Navigate to app folder:

`cd app`

Clone Metaplex CLI repo:

`git clone --branch v1.0.0 https://github.com/metaplex-foundation/metaplex.git ~/metaplex-foundation/metaplex `  

Insatll Metaplex CLI using yarn:

`yarn install --cwd ~/metaplex-foundation/metaplex/js/`

## Configure Solana Environment

Confirm Solana CLI is installed:

`solana --version`

Set environment:

`solana config set --url https://api.devnet.solana.com`

Generate Solana keypair:

`solana-keygen new --outfile ~/.config/solana/devnet.json`

Set keypair as default keypair:

`solana config set --keypair ~/.config/solana/devnet.json`

Review local Solana wallet address:

`solana address`

Update the wallet address in assests json metadata.

## Upload NFT's to Arweave using Metaplex CLI

Confirm Metaplex is installed:

`ts-node ~/metaplex-foundation/metaplex/js/packages/cli/src/candy-machine-cli.ts --version`

Upload NFT's to Arweave:

`ts-node ~/metaplex-foundation/metaplex/js/packages/cli/src/candy-machine-cli.ts upload ./assets --env devnet --keypair ~/.config/solana/devnet.json`

Verify upload:

`ts-node ~/metaplex-foundation/metaplex/js/packages/cli/src/candy-machine-cli.ts verify --keypair ~/.config/solana/devnet.json`

## Deploy Candy Machine to Metaplex Contract using Metaplex CLI

Deploy Candy Machine, `-p` sets the price in SOL:

`ts-node ~/metaplex-foundation/metaplex/js/packages/cli/src/candy-machine-cli.ts create_candy_machine --env devnet --keypair ~/.config/solana/devnet.json -p 1`

Take note of the `candy machine pubkey`.

## Set Drop Date using Metaplex CLI

`ts-node ~/metaplex-foundation/metaplex/js/packages/cli/src/candy-machine-cli.ts update_candy_machine --date "1 Dec 2021 00:12:00 GMT" --env devnet --keypair ~/.config/solana/devnet.json`

## Configure WebApp Environemnt

Open `.cache/devent-temp` to review.

Set `REACT_APP_CANDY_MACHINE_CONFIG` to `config` key in `.cache/devent-temp`.
Set `REACT_APP_CANDY_MACHINE_ID` to `candyMachineAddress` key in `.cache/devent-temp`.
Set `REACT_APP_TREASURY_ADDRESS` to `authority` key in `.cache/devent-temp`.
Set `REACT_APP_SOLANA_NETWORK` to `devnet`.
Set `REACT_APP_SOLANA_RPC_HOST` to `https://explorer-api.devnet.solana.com`