# Ethers Simple Storage

# Getting Started

`This code has been adapted for ethers 6.3.0`

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [Nodejs](https://nodejs.org/en/)
  - You'll know you've installed nodejs right if you can run:
    - `node --version` and get an ouput like: `vx.x.x`
- [Yarn](https://classic.yarnpkg.com/lang/en/docs/install/) instead of `npm`
  - You'll know you've installed yarn right if you can run:
    - `yarn --version` and get an output like: `x.x.x`
    - You might need to install it with npm
- [ganache](https://trufflesuite.com/ganache/)
  - You'll know you did it right if you can run the application.

## Setup

Clone this repo

```
git clone https://github.com/MMtis/ethers-simple-storage
cd ethers-simple-storage
```

Then install dependencies

```
yarn
```

### Typescript

The repo contains both JS and TS code versions with the required libraries.

## Usage

1. Run your ganache local chain, by hitting `quickstart` on your ganache application

> Save the workspace. This way, next time you open ganache you can start the workspace you've created, otherwise you'll have to redo all the steps below.

2. Copy the `RPC SERVER` sting in your ganache CLI, and place it into your `.env` file similar to what's in `.env.example`.


`.env` Example:

```
RPC_URL=http://0.0.0.0:8545
```

3. Hit the key on one of the accounts, and copy the key you see and place it into your `.env` file, similar to what you see in `.env.example`.


`.env` Example:

PRIVATE_KEY=11ee3108a03081fe260ecdc106554d09d9d1209bcafd46942b10e02943effc4a

You can also encypt your private key using the encryptKey script. To do that you need to create a password and run the command:

```
PRIVATE_KEY_PASSWORD= YOUR_PASSWORD node encryptKey.js
```
Or for TS
```
PRIVATE_KEY_PASSWORD= YOUR_PASSWORD ts-node encryptKeyTS.ts
```

4. Compile your Solidity code

Run

```
yarn compile
```

You'll see files `SimpleStorage_sol_SimpleStorage.abi` and `SimpleStorage_sol_SimpleStorage.bin` be created.

5. Run

```
node deploy.js or ts-node deployTS.ts (for TS)
```

Or if you are using the private key encryption

```
PRIVATE_KEY_PASSWORD=Your_Password node deploy.js or PRIVATE_KEY_PASSWORD=Your_Password ts-node deployTS.ts (for TS)
```

You could also just do `npx ts-node deploy.ts` if you are using npm.
For yarn use `yarn ts-node deploy.ts`.

### Deploying to a testnet

Make sure you have a [metamask](https://metamask.io/) or other wallet, and export the private key.

**IMPORTANT**

USE A METAMASK THAT DOESNT HAVE ANY REAL FUNDS IN IT. Just in case you accidentally push your private key to a public place. I _highly_ recommend you use a different metamask or wallet when developing.

1. [Export your private key](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key) and place it in your `.env` file, as done above.

2. Go to [Alchemy](https://alchemy.com/?a=673c802981) and create a new project on the testnet of choice (ie, Sepolia)
3. Grab your URL associated with the testnet, and place it into your `.env` file.
4. Make sure you have testnet ETH in your account. You can get some here ([sepolia faucets located here](https://sepoliafaucet.com/)). You should get testnet ETH for the same testnet that you made a project in Alchemy (ie, Sepolia)

5. Run

```
node deploy.js or ts-node deployTS.ts (for TS)
```

Or if you are using the private key encryption

```
PRIVATE_KEY_PASSWORD=Your_Password node deploy.js or PRIVATE_KEY_PASSWORD=Your_Password ts-node deployTS.ts (for TS)
```

### Typescript Differences

1. We installed `@types/fs-extra` and `@types/node`
2. We have a `tsconfig.json` file
3. We have to compile our ts code and then run our js code
