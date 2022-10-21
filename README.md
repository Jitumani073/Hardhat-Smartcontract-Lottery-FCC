# Hardhat Smartcontract Lottery FCC

A sample Raffle Contract.

This contract is for creating an untamperable decentralized smart contract.

This implements Chainlink VRF v2 and Chainlink Keepers.

## Usage

#### Deploy:

`yarn hardhat deploy`

#### Testing:

`yarn hardhat test`

#### Test Coverage:

`yarn hardhat coverage`

## Deployment to a testnet

#### 1. Setup environment variables

You'll want to set your `GOERLI_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file.

- `PRIVATE_KEY`: The private key of your account (like from [metamask](https://metamask.io/)).
- `GOERLI_RPC_URL`: This is url of the goerli testnet node you're working with. You can get setup with one for free from [Alchemy](https://www.alchemy.com/)

#### 2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH & LINK. You should see the ETH and LINK show up in your metamask. [You can read more on setting up your wallet with LINK.](https://docs.chain.link/docs/deploy-your-first-contract/#install-and-fund-your-metamask-wallet)

#### 3. Setup a Chainlink VRF Subscription ID

Head over to [vrf.chain.link](https://vrf.chain.link/) and setup a new subscription, and get a subscriptionId. You can reuse an old subscription if you already have one.

[You can follow the instructions](https://docs.chain.link/docs/vrf/v2/subscription/examples/get-a-random-number/) if you get lost. You should leave this step with:

- A subscription ID
- Your subscription should be funded with LINK
- Deploy
  In your `helper-hardhat-config.js` add your `subscriptionId` under the section of the chainId you're using

#### Then run:

`yarn hardhat deploy --network goerli`

And copy / remember the contract address.

#### 4. Add your contract address as a Chainlink VRF Consumer

Go back to [vrf.chain.link](https://vrf.chain.link/) and under your subscription add `Add consumer` and add your contract address. You should also fund the contract with a minimum of 1 LINK.

#### 5. Register a Chainlink Keepers Upkeep

[You can follow the documentation if you get lost.](https://docs.chain.link/docs/chainlink-automation/compatible-contracts/)

Go to [keepers.chain.link](https://automation.chain.link/new) and register a new upkeep. Choose `Custom logic` as your trigger mechanism for automation.

#### 6. Enter your raffle!

You're contract is now setup to be a tamper proof autonomous verifiably random lottery. Enter the lottery by running:

`yarn hardhat run scripts/enter.js --network goerli`

# Thank you!

