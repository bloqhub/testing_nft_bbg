# Getting started with building DApps

### Crypto wallet setup
We need to set up a crypto wallet that will act as a gateway to blockchain apps. [Metamask](https://metamask.io/) is one of the most popular and easy to use crypto wallets, so we'll be using that.

You can download Metamask using [this](https://metamask.io/download.html) link.
Make sure to install it and keep your seed phrases safe!

Metamask is able to connect and interact with the Ethereum chains, In this particular repo I've deployed the NFT contract in Binance Smart Chain Testnet, So you will have to add this network to metamask to communicate with the blockchain network.
To do this visit the [bsc testnet blockchain explorer](https://testnet.bscscan.com/) (A blockchain explorer is a place where you can view all the indexed data stored in the blockchain) and scroll to the bottom and click the "🦊Add BSC Network button" 

### Now you will need to get some Ether!

Ether is the currency that is used for paying for all the transactions in the blockchain. [ETH](https://coinmarketcap.com/currencies/ethereum/) is the ether in the Ethereum mainnet, [BNB](https://coinmarketcap.com/currencies/binance-coin/) is the ether in the Binance Smart Chain and so on.
Don't worry we are not going to exchange our fiat currency to get some ether for our network since we're just using testnet for testing. You will need to go to [ Binance Smart Chain Faucet](https://testnet.binance.org/faucet-smart) and paste your wallet address and get 1 BNB (Note that you can only do this once every 24h)

### Deploying your smart contract

There are multiple ways to deploy a smart contract, The simplest way is to use [remix](https://remix.ethereum.org/) as it allows you to create, deploy and interact with the smart contract all within the web browser without installing any dev dependencies in your local. All you need is your metamask to interact with the contract using injected web3.

I've already deployed the __BBG.sol__ smart contract in the BSC testnet network [0xbe1a1dc4126f73aeb6293cacab369daf56b1c0a5](https://testnet.bscscan.com/address/0xbe1a1dc4126f73aeb6293cacab369daf56b1c0a5) which is being interacted in the __index.html__

### Interacting with the smart contract

Most of the server logic and database is moved to the blockchain (But not every server logic since the data in the blockchain needs a transaction every time you need to change the state) but there is a lot of UI logic that is quite dynamic and needs to communicate with the blockchain to get the data.
We can use [web3.js](https://web3js.readthedocs.io/en/v1.5.2/) or [ethers.js](https://docs.ethers.io/v5/) if we're planning to use JavaScript in our frontend.
We can use the Contract's ABI methods to communicate with the deployed contract.
In this example, I've used the __mintNFT()__ method from our contract

Note: You will only be able to interact using your metamask if you run the webpage using some server (could be served using live-server). This is because the Metamask only injects the web3 in http/https protocols and not in static file:// protocols (At least that's what I feel!)
