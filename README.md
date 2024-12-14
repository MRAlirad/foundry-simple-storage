# Foundray Simple Storage

## Introduction

Throughout this course, you will acquire the skills you’ll need to start developing your smart contracts and protocols using the best web3 development tools and frameworks like _**Chainlink**_, _**Alchemy**_, and _**Foundry**_.

### What is Foundry?

Foundry is a relatively new but rapidly growing smart contract development framework known for its efficiency and modularity. The best short description of this powerful tool can be found in the [Foundry Book](https://book.getfoundry.sh/):

```Solidity
Foundry manages your dependencies, compiles your project, runs tests, deploys, and lets you interact with the chain from the command-line and via Solidity scripts.
```

Foundry has numerous pros, such as:

-   It **leverages Rust** for compilation, offering significantly faster build times compared to frameworks like Hardhat or Brownie.
-   It's entirely **Solidity-based**, eliminating the need to learn other programming languages
-   Its **documentation is comprehensive**.


## Foundry Setup Installation
Navigate to the [Foundry website](https://book.getfoundry.sh/getting-started/installation) and from the installation tab, fetch the command to install Foundry.

The command would look something like this:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

### Verifying Your Installation

After running the `curl` command, an output will appear at the bottom of your terminal indicating the detected shell and the fact that Foundry has been added to your `Path`.

For instance, the output can be something like this:

```bash
Detected your preferred shell is bashrc and added Foundry to Path run:source /home/user/.bashrcStart
a new terminal session to use Foundry
```

Now, simply type `foundryup` and `Enter` to install and update Foundry to the latest version. Whenever you want to install an update for Foundry, simply run `foundryup` again.

This will install four components: forge, cast, anvil, and chisel. To confirm the successful installation, run `forge --version`. You should get an output indicating the Forge version as shown below.

```bash
Forge version x.x.x
```

Most of the time the `bashrc` file gets loaded automatically. However, if this doesn't apply to your setup, the following lines can add the required command to the end of your `Bash profile`. This will ensure that your `bashrc` file loads by default.

```bash
cd ~
echo 'source /home/user/.bashrc' >> ~/.bash_profile
```

> this depends on your operating system, please check foundry docs to see detailed instructions.

## Create a new Foundry Project

The way you [create a new Foundry project](https://book.getfoundry.sh/projects/creating-a-new-project) is by running the `forge init` command. This will create a new Foundry project in your current working directory.

If you want Foundry to create the new project in a new folder type `forge init nameOfNewFolder`.

Keep in mind that by default `forge init` expects an empty folder. If your folder is not empty you must run `forge init --force .`

<img src='./images/create-first-project/Image1.png' alt='Image1' />

**But what does all this mean?**

`lib` is the folder where all your dependencies are installed, here you'll find things like:

-   `forge-std` (the forge library used for testing and scripting)
-   `openzeppelin-contracts` is the most battle-tested library of smart contracts
-   and many more, depending on what you need/install

`scripts` is a folder that houses all your scripts

`src` is the folder where you put all your smart contracts

`test` is the folder that houses all your tests

`foundry.toml` - gives configuration parameters for Foundry

Create new file named `SimpleStorage.sol` in the `src` folder and copy the code of `SimpleStorage` in it

## Improving Code Format in Visual Studio Code

When you first start, your code might just look like a whole bunch of dull, lifeless, white text.

This can be easily fixed by using one of the `Solidity` extensions. Out of all the Solidity extensions available in the Extensions tab (CTRL/CMD + SHIFT + X) the following are worth mentioning:

1. [Solidity by Juan Blanco](https://marketplace.visualstudio.com/items?itemName=JuanBlanco.solidity), the most used Solidity extension out there.
2. [Solidity by Nomic Foundation](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity) is Patrick's favorite Solidity extension. The rest of the course will be displaying this extension.
3. [Solidity Visual Developer](https://marketplace.visualstudio.com/items?itemName=tintinweb.solidity-visual-auditor) is another popular choice.

**NOTE**: If the code remains unhighlighted despite having installed the extension, there's a quick solution to that. Press `Command + Shift + P`, or `Control + Shift + P` on Windows. This opens up the command bar. In the command bar, type in "Settings" and select "Preferences: Open User Settings (JSON)".

If you have nothing in there, create a new setting by typing in:

```Solidity
{
  "editor.defaultFormatter": "NomicFoundation.hardhat"
}
```

Use:

`"editor.defaultFormatter": "tintinweb.solidity-visual-auditor"` for Solidity Visual Developer

or

`"editor.defaultFormatter": "JuanBlanco.solidity"` for Solidity by Juan Blanco

### Other interesting extensions

In the previous lesson, we mentioned a file called `foundry.toml`. This also has an extension that formats it to make it easier to read. Please install [Even Better TOML](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml).

Another indispensable extension is [Inline Bookmarks](https://marketplace.visualstudio.com/items?itemName=tintinweb.vscode-inline-bookmarks).

The Inline Bookmarks plugin facilitates bookmarking the actual code. The extension can be used for document review, auditing, log analysis, and keeping track of development notes and to-do lists. You may share your notes and bookmarks with others with ease because they are saved with your files.

The following default trigger words/tags are configured by default:

```Solidity
@todo - (blue) General ToDo remark.
@note - (blue) General remark.
@remind - (blue) General remark.
@follow-up - (blue) General remark.
@audit - (red) General bookmark for potential issues.
@audit-info - (blue) General bookmark for information to be noted for later use.
@audit-ok - (green) Add a note that a specific line is not an issue even though it might look like.
@audit-issue - (purple) Reference a code location an issue was filed for.
```

You can fully customize the colors!

Remember these! They will be very handy in developing and especially in auditing projects.

More details are available [here](https://github.com/tintinweb/vscode-inline-bookmarks).

Next comes the fun part! Let's compile our contract using Foundry!

## Compiling Smart Contracts: A Guide to the Foundry Console Compilation Process

Open a new terminal. Type in `forge build` or `forge compile` to compile the smart contracts in your project.

Once the compiling is finished, you'll see some new folders in the Explorer tab on the left side. One of them is a folder called `out`. Here you'll be able to find the [ABI](https://docs.soliditylang.org/en/latest/abi-spec.html) of the smart contract together with the [Bytecode](https://www.geeksforgeeks.org/introduction-to-bytecode-and-opcode-in-solidity/) and a lot of useful information.

The `cache` folder also appears. Generally, this folder is used to store temporary system files facilitating the compilation process. But for this course, you can safely ignore it.

## Deploy a smart contract locally using Anvil

There are multiple ways and multiple places where you could deploy a smart contract.

While developing using the Foundry framework the easiest and most readily available place for deployment is Anvil.

Anvil is a local testnet node shipped with Foundry. You can use it for testing your contracts from frontends or for interacting over RPC.

To run Anvil you simply have to type `anvil` in the terminal.

<img src='./images/deploy-smart-contract-anvil/anvil.png' alt='anvil' />

You now have access to 10 test addresses funded with 10\_000 ETH each, with their associated private keys.

This testnet node always listens on `127.0.0.1:8545` this will be our `RPC_URL` parameter when we deploy smart contracts here. More on this later!

More info about Anvil is available [here](https://book.getfoundry.sh/reference/anvil/).

Anvil will be used throughout the course to deploy and test our smart contracts, but before that, let's quickly check an intermediary step.

### Ganache

_Ganache is a glaze, icing, sauce, or filling for pastries usually made by heating equal parts weight of cream and chopped chocolate, warming the cream first, then pouring it over the chocolate._

Wait, not that ganache! The other ganache:

Ganache is a personal blockchain for rapid Ethereum and Filecoin distributed application development. You can use Ganache across the entire development cycle; enabling you to develop, deploy, and test your dApps in a safe and deterministic environment.

Please download Ganache from [here](https://archive.trufflesuite.com/ganache/).

For people using Windows WSL please read [this](https://github.com/Cyfrin/foundry-simple-storage-f23?tab=readme-ov-file#windows-wsl--ganache). Using Ganache in this environment is not the easiest thing to do. We are not going to use this in the future, so don't worry if you can't configure it properly.

Hit `Quickstart Ethereum`. Voila! A brand new blockchain. We get some addresses, that have balances and private keys.

### Configuring MetaMask

To deploy to a custom network (like your localhost), you'll need MetaMask. MetaMask is a popular cryptocurrency wallet and browser extension that allows users to interact with the Ethereum blockchain and its ecosystem. If you don't have it download it from [here](https://metamask.io/download/)

Follow these steps:

1. Open MetaMask.

2. Click the three little dots and select 'Expand View'.

3. Go to 'Settings', then 'Networks'.

4. Here, you'll see the list of networks (Ethereum, Mainnet, etc.) with plenty of details about each one. Locate the RPC URL - this is key.

The RPC URL is essentially the endpoint we make API calls to when sending transactions. For every blockchain transaction you execute, you're making an API to whatever is in here.
To send a transaction to your custom blockchain, you need to add it as a network:

1. Click on 'Add a Network'

2. Scroll to the bottom of the list of networks.

3. Hit 'Add a Network manually'.

4. Enter the details of your local network

	Network name: `Localhost`

	New RPC URL: Ganache`http://127.0.0.1:7545` or Anvil `http://127.0.0.1:8545` (make sure you always add `http://`) - these two could differ on your machine, please consult the Ganache UI or Anvil terminal for the exact RPC URL.

	Chain ID: Ganache `5777`(sometimes `1337`) or Anvil `31337` - these two could differ on your machine, please consult the Ganache UI or Anvil terminal for the exact Chain ID.

	Currency symbol: ETH

	plorer URL: - (we don't have a block explorer for our newly created blockchain, which will most likely disappear when we close the VS Code / Ganache app)

Great! Now that we configured our local network, the next step is to add one of the accounts available in Ganche or Anvil into our MetaMask. [This is done as follows](https://support.metamask.io/hc/en-us/articles/360015489331-How-to-import-an-account#h_01G01W07NV7Q94M7P1EBD5BYM4):

1. Click the account selector at the top of your wallet.

2. Click `Add account or hardware wallet`.

3. Click `Import account`

4. You will be directed to the Import page. Paste your Ganache/Anvil private key. Click `Import`.

**NOTE: Do not use this account for anything else, do not interact with it or send things to it on mainnet or any other real blockchain, use it locally, for testing purposes. Everyone has access to it.**

## Deploy a smart contract locally using Forge

To find out more about forge's capabilities type

```Solidity
forge --help
```

Out of the resulting list, we are going to use the `create` command.

Type `forge create --help` in the terminal or go [here](https://book.getfoundry.sh/reference/forge/forge-create) to find out more about the available configuration options.

Try running `forge create SimpleStorage`. It should fail because we haven't specified a couple of required parameters:

1. `Where do we deploy?`

2. `Who's paying the gas fees/signing the transaction?`

Let's tackle both these questions.

As you've learned in the previous lessons, each blockchain (private or public) has an RPC URL (RPC SERVER) that acts as an endpoint. When we tried to deploy our smart contract, forge tried to use `http://localhost:8545/`, which doesn't host any blockchain. Thus, let's try to deploy our smart contract specifying the place where we want to deploy it.

Please start Ganache and press `Quickstart Ethereum`. Copy the RPC Server `HTTP://127.0.0.1:7545`. Let's run our forge create again specifying the correct rpc url.

```Solidity
forge create SimpleStorage --rpc-url http://127.0.0.1:7545
```

This again failed, indicating the following:

```Solidity
Error accessing local wallet. Did you set a private key, mnemonic or keystore?
```

Try the following command:

```Solidity
forge create SimpleStorage --rpc-url http://127.0.0.1:7545 --interactive
```

You will be asked to enter a private key, please paste one of the private keys available in Ganache. When you paste a key you won't see the text or any placeholder symbols, just press CTRL(CMD) + V and then ENTER.

Voila!

<img src='./images/deploy-smart-contract-forge/forge.png' alt='forge' />

ou can go to Ganache and check the `Blocks` and `Transactions` tabs to see more info about what you just did.

From now on, everything we deploy shall be done on Anvil. But if you like Ganache more, feel free to use that.

Do the following:

1. Run `clear`
2. Run `anvil`
3. Create a new terminal by pressing the `+` button
4. Copy one of the private keys from the anvil terminal
5. Run `forge create SimpleStorage --interactive`
	We don't need to specify an `--rpc-url` this time because forge defaults to Anvil's RPC URL.
6. Go to the Anvil terminal and check the deployment details:

```Solidity
	Transaction: 0x40d2ca8f0d680f098c7d5e3c127ef1ce1207ef439ba6e163c2042483e15998a6
	Contract created: 0x5fbdb2315678afecb367f032d93f642f64180aa3
	Gas used: 357076

	Block Number: 1
	Block Hash: 0x85a56c0b8f166e86d1cce65412615e0d9a72972e04b2488023275131ea27330a
	Block Time: "Mon, 15 Apr 2024 11:50:55 +0000"

```

The more explicit way to deploy using `forge create` is as follows:

```Solidity
forge create SimpleStorage --rpc-url http://127.0.0.1:8545 --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```

We included the `--rpc-url` to not count on the default and the `--private-key` to not use the `--interactive` option anymore.

We learned a very important thing, how to deploy a smart contract on two local blockchains. But what comes next is one of the most important if not the _**MOST IMPORTANT**_ aspects you will learn here: _**Private key safety**_

## Private key safety

Having a private key in plain text is extremely bad. The private key(s) we used in the last lesson are well-known keys for local testing, you shouldn't use those on mainnet and keeping them in plain text is ok, but any other private key should be kept hidden, especially your production key or key's associated with accounts that hold crypto.

Moreover, it's very bad to have private keys in bash history (hit the up arrow and see the key you used to deploy).

You can delete your history by typing:

```Solidity
history -c
```

Hacking private keys is one of the most important reasons people and projects lose absurd amounts. You don't even need to look that deep to find titles like this:

[The Ronin hack](https://www.halborn.com/blog/post/explained-the-ronin-hack-march-2022) - Social engineering of private keys

[Early Crypto Investor Bo Shen Says He Lost \$42 Million in Wallet Hack](https://www.bnnbloomberg.ca/early-crypto-investor-bo-shen-says-he-lost-42-million-in-wallet-hack-1.1850446)

[The \$477 million FTX hack](https://www.elliptic.co/blog/the-477-million-ftx-hack-following-the-blockchain-trail) where `The new CEO of FTX revealed that private keys allowing access to the firm’s crypto assets were stored in unencrypted form, and a former employee disclosed that over $150 million was stolen from Alameda Research, due to poor security. `;

In the following lessons, we'll learn how to access RPC URLs for free using Alchemy for any blockchain. We will also delve into exploring safer methodologies for dealing with private keys. Stay tuned!

## Deploy a smart contract locally using Anvil

Deploying a smart contract via scripting is particularly handy because it provides a consistent and repeatable way to deploy reliably and its features enhance the testing of both the deployment processes and the code itself.

There's a strong chance that you like the command-line approach, but scripting enriches the whole deployment process, bringing in more functionality and an ease of use second to none.

Foundry eases the whole process since it is written in Solidity. This means our deployment scripts will also be written in Solidity. It is essential to distinguish Solidity as a contract language from Solidity as a scripting language. Foundry also incorporates elements that enhance our Solidity experience beyond the smart contracts realm. So, let's get started on creating a script to deploy our simple storage contract.

In Foundry we keep our scripts in the `script` folder.

Please create a new file called `DeploySimpleStorage.s.sol`.

Using `.s.sol` as a suffix is a naming convention for Foundry scripts, in future lessons, when we'll write Foundry tests, these will bear the suffix of `.t.sol`.

For more best practice info regarding Foundry scripts please click [here](https://book.getfoundry.sh/tutorials/best-practices#scripts).

Open the newly created file. Here we'll write a solidity script for deploying our SimpleStorage contract.

Type the following:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.19;

contract DeploySimpleStorage {
    
}
```

The first two lines are pretty self-explanatory.

We declare the new contract, named `DeploySimpleStorage`

For it to be considered a Foundry script and to be able to access the extended functionality Foundry is bringing to the table we need to import `Script` from `"forge-std/Script.sol"` and make `DeploySimpleStorage` inherit `Script`.

**NOTE**: `forge-std` also called Forge Standard Library is a collection of pre-written Solidity contracts designed to simplify and enhance scripting and testing within the Foundry development framework.

Furthermore, to be able to deploy `SimpleStorage` we also need to import it by typing `import {SimpleStorage} from "../src/SimpleStorage.sol";`

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.19;

import {Script} from "forge-std/Script.sol";
import {SimpleStorage} from "../src/SimpleStorage.sol";

contract DeploySimpleStorage is Script {
    
}
```

Every script needs a main function, which, according to the best practice linked above is called `run`. Whenever you run `forge script` this is the function that gets called.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.19;

import {Script} from "forge-std/Script.sol";
import {SimpleStorage} from "../src/SimpleStorage.sol";

contract DeploySimpleStorage is Script {
    function run() external returns (SimpleStorage) {
        vm.startBroadcast();

        SimpleStorage simpleStorage = new SimpleStorage();

        vm.stopBroadcast();
        return simpleStorage;
    }
}
```

`run` is an external function that will return the `SimpleStorage` contract.

In the Run function, we are going to use a distinctive keyword: `vm`. Foundry has a distinctive feature known as cheat codes. The `vm` keyword is a cheat code in Foundry, and thereby only works in Foundry.

`vm.startBroadcast` indicates the starting point for the list of transactions that get to be sent to the `RPC URL`;

Similarly, `vm.stopBroadcast` indicates the ending point of the list of transactions that get to be sent to the `RPC URL`;

Between those two we write:

`SimpleStorage simpleStorage = new SimpleStorage();`

The `new` keyword is used to create a new smart contract in Solidity.

We end the function with `return simpleStorage;`.

Please select the `Anvil` terminal and press `CTRL(CMD) + C` to stop it. Now run the following command:

```bash
forge script script/DeploySimpleStorage.s.sol
```

This should go through without any errors, but if you hit some errors related to `incompatible solidity versions in various files` please ensure that both the `SimpleStorage.sol` and `DeploySimpleStorage.s.sol` use `pragma solidity 0.8.19;`

If you want to further extend your knowledge about scripting please go [here](https://book.getfoundry.sh/tutorials/solidity-scripting?highlight=scr#solidity-scripting)

You should get the following output:

```text
[⠆] Compiling...
[⠔] Compiling 2 files with 0.8.19
[⠒] Solc 0.8.19 finished in 1.08s
Compiler run successful!
Script ran successfully.
Gas used: 338569

== Return ==
0: contract SimpleStorage 0x90193C961A926261B756D1E5bb255e67ff9498A1

If you wish to simulate on-chain transactions pass a RPC URL.
```

**The million-dollar question**: If we didn't pass an RPC URL, where did this deploy to?

If the RPC URL is not specified, Foundry automatically launches an Anvil instance, runs your script (in our case deployed the contract) and then terminates the Anvil instance.

Run the `anvil` command in the terminal, open up a new terminal and type the following:

```bash
forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545
```

To get the following output:

```text
No files changed, compilation skipped
EIP-3855 is not supported in one or more of the RPCs used.
Unsupported Chain IDs: 31337.
Contracts deployed with a Solidity version equal or higher than 0.8.20 might not work properly.
For more information, please see https://eips.ethereum.org/EIPS/eip-3855
Script ran successfully.

== Return ==
0: contract SimpleStorage 0x34A1D3fff3958843C43aD80F30b94c510645C316

## Setting up 1 EVM.

==========================

Chain 31337

Estimated gas price: 2 gwei

Estimated total gas used for script: 464097

Estimated amount required: 0.000928194 ETH

==========================

SIMULATION COMPLETE. To broadcast these transactions, add --broadcast and wallet configuration(s) to the previous command. See forge script --help for more.
```

**Another million-dollar question**: Is it deployed now?

Answer: No, the output indicates this was a simulation. But, we got a new folder out of this, the `broadcast` folder contains information about different script runs in case we forget details.

Hit the up arrow key and add `--broadcast --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` at the end.

Our contract is now successfully deployed! Fantastic!

Switch to the `anvil` terminal where you'll see:

```text
	Transaction: 0x73eb9fb4ef7b159e03c50d669c42e2ec4eeaa9358bea0a710cb07168e5192570
	Contract created: 0x5fbdb2315678afecb367f032d93f642f64180aa3
	Gas used: 357088

	Block Number: 1
	Block Hash: 0x8ea564f146e04bb36fc27f0b491223a023b5882d2fcfce3ff85e0dd152e611e4
	Block Time: "Tue, 16 Apr 2024 13:39:51 +0000"
```

## More about blockchain transactions

On the left side of your screen, in the Explorer tab, you'll find a folder called `broadcast`. Foundry saves all your blockchain interactions here. The `dry-run` folder is used for interactions you made when you didn't have a blockchain running (remember that time when we deployed our contract without specifying an `--rpc-url`). Moreover, the recordings here are separated by `chainId`.

**Note**: The `chainId` is a unique identifier assigned to a specific blockchain network. It is used to distinguish one blockchain from another and is a crucial parameter for ensuring the security and integrity of transactions and interactions on the blockchain.

Click on `run-latest.json`.
Here we can find more details about the last deployment script we ran in our previous lesson. It will show things like `transactionType`, `contractName` and `contractAddress`. Moreover, in the `transaction` section, you can see what we actually sent over to the RPC URL:

```javaScript
"transaction": {
	"from": "0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266",
	"to": null,
	"gas": "0x714e1",
	"value": "0x0",
	"input": "0x608060...c63430008130033",
	"nonce": "0x0",
	"chainId": "0x7a69",
	"accessList": null,
	"type": null
}
```

Let's go through each of these:

* `from` is self-explanatory, it's the address we used to sign the transaction;
* `to` is the recipient, in our case is null or address(0), this is the standard destination for when new smart contracts are deployed;
* `gas` is the amount of gas spent. You will see the hex value `0x714e1` (or any other value represented in hex format);

**Quick tip**: Normal humans can't understand hex values like the one indicated above, but there's a quick way to convert these into usual numbers. Run the following command in your terminal: `cast --to-base 0x714e1 dec`. `cast` is a very versatile tool provided by Foundry, type `cast --help` in your terminal to find out more, or go [here](https://book.getfoundry.sh/reference/cast/cast).

* `value` is the transaction value, or the amount of ETH we are sending over. Given that this transaction was made to deploy a contract, the value here is `0x0` or `0`, but we could have specified a value and that would have been the initial balance of the newly deployed contract;

* `data` in this case is the contract deployment code and the contract code. In the excerpt above this was truncated;

* `nonce` is a unique identifier assigned to each transaction sent from a specific account. The nonce is used to ensure that each transaction is processed only once and to prevent replay attacks. `nonce` is incremented with every single transaction;

* `accessList` is a feature of Ethereum to optimize the gas cost of transactions. It contains a list of addresses and associated storage keys that the transaction is likely to access, allowing the EVM to more efficiently compute the gas cost of storage access during the transaction's execution;

* `type` please ignore this for now.

There are other values that play an important part that weren't presented in that list, namely the `v`, `r`, and `s`. These are components of a transaction's signature, which are used to validate the authenticity and integrity of the transaction.

Whenever we send a transaction over the blockchain there's a signature happening, that's where we use our `private key`.

**Important:** Every time you change the state of the blockchain you do it using a transaction. The thing that indicates the change is the `data` field of a transaction. Deployment bytecode, contract bytecode and OPCODEs will be tackled in a future lesson.

## Private key safety - pt2

We deployed `SimpleStorage` using the following command:

```Solidity
forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```

Having our private key in plain text is very bad. What can we do to avoid this, except using the `--interactive` parameter, because we don't want to keep copy-pasting our private key?

**BIG BOLDED DISCLAIMER: What we are about to do is fine for development purposes, do not put a real key here, it very terrible for production purposes.**

Create a new file in the root of your project called `.env`. Then, go the `.gitignore` file and make sure `.env` is in there.

The `.env` file will host environment variables. Variables that are of a sensitive nature that we don't want to expose in public.

Open the file and put the following in it:

```Solidity
PRIVATE_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
RPC_URL=http://127.0.0.1:8545
```

Next run `source .env`. This adds the above-mentioned environment variables into our shell. Now run `echo $PRIVATE_KEY` or `echo $RPC_URL` to check if the values are stored in the shell.

Now we can safely replace the parameters in our `forge script` command:

```Solidity
forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
```

This doesn't only hide your private key from plain sight in the command line but also facilitates faster terminal usage, imagine you'd have to copy-paste the `http://127.0.0.1:8545` RPC URL over and over again. It's cleaner this way.

But yes, now we have the private key in plain text in the `.env` file, that's not good.

### How to handle this problem with production code?

Foundry has a very nice option called `keystore`. To read more about it type `forge script --help` in your terminal. Using `forge script --keystore <PATH>` allows you to specify a path to an encrypted store file, encrypted by a password. Thus your private key would never be available in plain text.

Let's agree to the following:

1. For testing purposes use a `$PRIVATE_KEY` in an `.env` file as long as you don't expose that `.env` file anywhere.
2. Where real money is involved use the `--interactive` option or a [keystore file protected by a password](https://github.com/Cyfrin/foundry-full-course-f23?tab=readme-ov-file#can-you-encrypt-a-private-key---a-keystore-in-foundry-yet).

There's one more thing about storing keys in a `.env` file. Please take a look at the ["THE .ENV PLEDGE"](https://github.com/Cyfrin/foundry-full-course-f23/discussions/5). Read it, understand it and comment `I WILL BE SAFE`. Tweet it, Tiktok it, blog about it, make an Insta story about it, print it and put it on your fridge and share some copies with your neighbors. Please stay safe!


## Never use a Env file

### Encrypting your Keys Using ERC2335

For now, let's pretend our private key is this:

`0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` (key 0 from Anvil)

Type the following command in your terminal:

```Solidity
cast wallet import nameOfAccountGoesHere --interactive
```

Ideally, you don't do this in your VS Code.

You will be asked for your private key and a password to secure it. You will do this only once, which is amazing!

If you remember, last lesson we deployed running the following command:

```Solidity
forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
```

Now that we configured our wallet we can deploy as following:

```Solidity
forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --account nameOfAccountGoesHere --sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
```

You will be asked for your password. You won't be able to deploy without your password.

To see all the configured wallets you can call the following: `cast wallet list`.

Clear your history so your private key won't randomly remain there using the following command: `history -c`.

***Stay safe! * Don't lose your keys. If you are seeing your private key in plain text, you are doing something wrong.***


## Interacting with a smart contract using the CLI

Foundry has a built-in tool known as `Cast`. `Cast` comes loaded with numerous commands to interact with. Learn more about them by typing `cast --help`. One such useful command is `send` which is designed to sign and publish a transaction. To view help about `send`, type `cast send --help`.

To use `send` we need a signature and some arguments.

Please call the following in your terminal:

**Note**: Down below use the address you copy-pasted from your terminal, there's a chance it will be different than the one mine was deployed.

```Solidity
cast send 0x5FbDB2315678afecb367f032d93F642f64180aa3 "store(uint256)" 1337 --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

**What did we just do?**

Let's break it down:

* `cast send` is the command we used to sign and publish our transaction;
* `0x5FbDB2315678afecb367f032d93F642f64180aa3` or any other address is the target of our `cast send`, the contract we are interacting with;
* `"store(uint256)"` is the [signature of the function](https://ethereum.stackexchange.com/questions/135205/what-is-a-function-signature-and-function-selector-in-solidity-and-evm-language) we are calling.
* `1337` is the number we pass to the `store` function. As we can see in the function signature, we are expected to provide an `uint256` input. You can obviously provide any number you want, as long as it fits `uint256`.
* you already know what `--rpc-url $RPC_URL --private-key $PRIVATE_KEY` are. The place where we send and the private key we use to sign.

### Reading information from the blockchain

`cast` conveniently provides a way to read information stored on the blockchain. Type `cast call --help` in your terminal to find out more. It works similarly to `send`, where you have to provide a signature and some arguments. The difference is you are only peering into the storage, not modifying it.

Call the following command in your terminal:

```Solidity
cast call 0x5FbDB2315678afecb367f032d93F642f64180aa3 "retrieve()"
```

We receive back the following:

```Solidity
0x0000000000000000000000000000000000000000000000000000000000000539
```

This represents a hex value. In the previous lessons, we learned how to convert this to a normal number.

Type the following command in your terminal:

```Solidity
cast --to-base 0x0000000000000000000000000000000000000000000000000000000000000539 dec
```

And surprise, surprise, `1337` came back.

## Deploying a smart contract on testnet (Sepolia)

Clearly, we need an actual testnet for a real network. But our trusty MetaMask has built-in Infura connections that are incompatible. Why? Because they're tailored specifically for MetaMask. Hence, we need our own Remote Procedure Call (RPC) URL.

### Creating our Own RPC URL for a Testnet

_To create one, we could run our own blockchain node, but let's be honest — many folks prefer avoiding that route. Instead, we utilize Node as a Service (NaaS) applications to expedite the process._

One promising option is using Alchemy - a free NaaS platform that we can send the transactions to. This procedure resides within the _Deploying to Testnet or Mainnnet_ section in the full course repo of the Foundry. and creating a new app.

### Altering our Private Key

we should use one of our MetaMask private keys.

### Executing the Transaction

With our Sepolia RPC URL and private key from MetaMask, executing a transaction now becomes tremendously easier.

```bash
source .env
forge script script/deploySimpleStorage.s.sol --rpc-url=$Sepolia_RPC_URL --private-key=$PRIVATE_KEY --broadcast
```

This command deploys our contract to the testnet, and we can monitor the transaction on our Alchemy dashboard.

We soon find that our contract, Simple Storage, has been deployed on the Sepolia chain. We can grab our transaction hash and input it into Sepolia etherscan IO to confirm the successful transaction.

After we refresh our Alchemy dashboard, we'll verify the requests sent and track the ETH send raw transaction that transmitted our transaction to the blockchain.

## Formatting

Forge has a built-in format command that will automatically format all our Solidity files according to Forge's default style.

```bash
forge fmt
```
