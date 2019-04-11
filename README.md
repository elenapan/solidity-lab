# Description
This repo includes the Truffle configuration files needed for deploying a smart contract either to a local blockchain generated by Ganache, or to the Ropsten Test Network.

Only the needed files are uploaded here. You will have to initialize a truffle project first, and then copy the contents of this repo inside it.

A sample smart contract is also included.

You can find the deployed contract on Ropsten at [0xb40857c01d2cb956b9f3e2cccd0190a56a1d3a31](https://ropsten.etherscan.io/address/0xb40857c01d2cb956b9f3e2cccd0190a56a1d3a31).

# Instructions (for Linux based systems)
- Install Truffle:

```shell
sudo apt install npm # Replace 'apt' with your distribution's package manager if needed
sudo npm install -g truffle
```

- Download the Ganache .AppImage from [here](https://truffleframework.com/ganache) and make it executable:

```shell
chmod +x Ganache-2.0.0.AppImage # Your version might be different
```

- Create a new project directory, initialize truffle and install `truffle-hdwallet-provider`:

```shell
mkdir my_truffle_project && cd my_truffle_project
npm init # Optional: Spam the enter key to accept the default/empty values.
truffle init
npm install truffle-hdwallet-provider
```

- Clone this repo somewhere and copy the files inside your project directory:

```shell
git clone https://github.com/elenapan/truffle-lab.git
cp -r truffle-lab/* /path/to/my_truffle_project
```

- Install [Metamask](https://metamask.io/) on your browser, create a Metamask wallet and save your **mnemonic** (12 word string) somewhere.

- Register an account on [Infura](https://infura.io/) and create a new project.

- Edit `truffle-config.js` in your project directory and paste your own mnemonic and Infura endpoint in the respective variables (remove the `<` and `>`):

```
// Place your own mnemonic here
var mnemonic = "<YOUR 12 WORD MNEMONIC HERE: orange apple banana ...>";
// Place your own infura endpoint URL for Ropsten here
var infura_endpoint = "https://ropsten.infura.io/v3/<YOUR INFURA PROJECT ID HERE>"
```

- Request some Ether on the [Ropsten Ethereum Faucet](https://faucet.ropsten.be/) by pasting your address generated by Metamask in the input box.

# Deployment
After following the instructions above, you should be ready to deploy your smart contract.

Assuming that you have `cd`ed into your project directory:

### Deploying on Ganache
- Launch Ganache:

```shell
/path/to/your/Ganache-2.0.0.AppImage
```

- Compile contract:

```
truffle compile
```

- Deploy contract:

```
truffle migrate
```

   or

```
truffle deploy
```
The two commands above are equivalent.

Note: You can use the flags `--reset --all` in order to force truffle to compile your contract from scratch before deploying (regardless whether it is needed or not).

```
truffle deploy --reset --all
```

- Run console

```
truffle console
```

### Deployment on Ropsten Test Network
- Compile contract:

```
truffle compile
```

- Deploy contract:

```
truffle migrate --network ropsten
```

   or

```
truffle deploy --network ropsten
```

- Run console

```
truffle console --network ropsten
```

# Cheatsheet for Truffle console
- Get accounts:

```
accounts = await web3.eth.getAccounts()
```

- Print accounts:

```
accounts
```

- Print specific account (e.g. 4):

```
accounts[4]
```

- Init contract instance:

```
c = await MyContract.deployed()
```

- Get contract address

```
c['address']
```

- Access public variables with their getter method:

```
await c.posts(0)
```

- Call functions:

```
await c.createNewPost("some title", "some url")
await c.createNewPost("some title", "some url", {from: accounts[3], gas: 400000})
await c.getNumberOfPosts()
```

# Tools / Frameworks / Services used in this lab
- [Truffle](http://truffleframework.com/)
- [Ganache](https://truffleframework.com/ganache)
- [Metamask](https://metamask.io/) *(optional)*
- [Infura](https://infura.io/)
- [Ropsten Ethereum Faucet](https://faucet.ropsten.be/)
- [Ropsten Etherscan](https://ropsten.etherscan.io)

# Useful links
- [Solidity Documentation](http://solidity.readthedocs.io/)
- [web3.js Documentation](https://web3js.readthedocs.io/en/1.0/)
- [Cryptozombies: Online Solidity Course](http://cryptozombies.io/)
- [Contract Oriented Programming I](https://github.com/androlo/solidity-workshop/blob/master/tutorials/2016-06-30-contract-oriented-programming-I.md) *(old but still useful)*
- [Contract Oriented Programming II](https://github.com/androlo/solidity-workshop/blob/master/tutorials/2016-07-02-contract-oriented-programming-II.md)
- [Truffle Boxes (Templates)](https://truffleframework.com/boxes)
- [Truffle Tutorial: Pet shop](https://truffleframework.com/tutorials/pet-shop)
- [Truffle: Deploy contracts using Infura](https://truffleframework.com/tutorials/using-infura-custom-provider)

