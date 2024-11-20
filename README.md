# Foundray Simple Storage

## Introduction

Welcome to Foundry 101. Throughout this course, you will acquire the skills you’ll need to start developing your smart contracts and protocols using the best web3 development tools and frameworks like _**Chainlink**_, _**Alchemy**_, and _**Foundry**_.

### What is Foundry?

Foundry is a relatively new but rapidly growing smart contract development framework known for its efficiency and modularity. The best short description of this powerful tool can be found in the [Foundry Book](https://book.getfoundry.sh/):

```Solidity
Foundry manages your dependencies, compiles your project, runs tests, deploys, and lets you interact with the chain from the command-line and via Solidity scripts.
```

Please take a moment to bookmark the [Foundry Book](https://book.getfoundry.sh/). It is the most comprehensive resource that has the answers to all your questions. It will be handy along the way.

Foundry has numerous pros, such as:

-   It **leverages Rust** for compilation, offering significantly faster build times compared to frameworks like Hardhat or Brownie.
-   It's entirely **Solidity-based**, eliminating the need to learn other programming languages
-   Its **documentation is comprehensive**.

## Development environment setup (Windows)

Download VS Code from [here](https://code.visualstudio.com/).

The setup is straightforward.
If this is your first time using VS Code spend some time and navigate through the "Get Started with VS Code" instructions. These valuable tips could clear many hurdles in your upcoming coding adventures. Moreover, to get an even better grasp on using VS Code, consider going through the [Visual Studio Code Crash Course](https://www.youtube.com/watch?v=WPqXP_kLzpo) from freeCodeCamp.

### VS Code terminal

VS Code has a built-in terminal emulator, often simply referred to as the VS Code terminal. It provides a command-line interface (CLI) environment directly within VS Code, allowing you to interact with your operating system and run various tools and utilities.

You can open up multiple terminals at the same time running different shells ranging from bash, Powershell, WSL and many more depending on what you have configured.

Use the `+` button to create a new terminal or the trash button to kill the current terminal.

Whether you are learning **Foundry** for development work or security work, moving fast is one of the keys to efficiency. VS Code is very versatile in terms of keyboard shortcuts, you can learn more [here](https://code.visualstudio.com/docs/getstarted/keybindings).

### What is WSL?

**WSL** stands for **Windows Subsystem for Linux**. It's a feature introduced by Microsoft that allows you to run a Linux environment directly on your Windows machine. This means you can use familiar Linux command-line tools and applications alongside your existing Windows programs. To ensure that your code runs on various machines using Unix-based systems like Mac and Linux, you'll find WSL to be immensely beneficial.

### How to install WSL?

Installing WSL is very easy, just open your Windows Terminal (comes preinstalled in Windows 11, available on Microsoft Store on Windows 10) and type:

```Solidity
wsl --install
```

After your system reboots, the Terminal will open automatically and proceed with the installation.

You will be asked to provide a new UNIX username and an associated password.

### Making Visual Studio Code Compatible with WSL

The next step is to ensure our VS Code is compatible with WSL.

Open up VS Code and navigate to the Extensions tab. Here, look for the Remote Development extensions and proceed to install each of them. This will enable VS Code to operate with WSL seamlessly. A new icon will appear on the bottom left of the screen called `Open a Remote Window`.

There's even an easier way to connect:

1. In the Windows Terminal, open up a new Ubuntu terminal.
2. Create a new folder by typing in:

```Solidity
mkdir solidity-course
```

1. Change the directory into the newly created folder

```Solidity
cd solidity-course/
```

1. Open VS Code inside the folder by typing in

```Solidity
code .
```

1. WIN! You just created a new instance of VS Code that uses WSL. Everything is correct if on the bottom left of your screen you see a small banner with the text `WSL Ubuntu`.

**Important: When you conduct your projects from a folder inside Windows (ex. Development) inside your documents, it's crucial to know that the WSL console will only access local files inside the WSL instance. Therefore, it's recommended to keep files inside the WSL instance for faster communication and convenience.**

### Git installation

Whether you have it and it needs to be updated or you need to perform a fresh install the best way to approach this is by visiting the [Git Book](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and following the instructions there.

Check your git installation calling

```Solidity
git --version
```

Amazing work! You're ready for the next lesson.

## Develop in the cloud using Gitpod

**BIG BOLDED DISCLAIMER: This is not the ideal way to develop smart contracts. While using Gitpod you should never share private information, like a key or a secret phrase. That's if you like to continue being the owner of the associated accounts.**

Gitpod is an online platform that provides cloud-based, pre-configured development environments specifically designed for working with Git repositories. It's similar to Remix IDE, but it allows you to run VS Code in a browser, on a remote server.

Go to [Gitpod's website](https://gitpod.io/login/) and click `Continue with Github`. After that, you'll be able to create a new workspace, starting from a Github repository, using a stable version of VS Code.

You'll be amazed to find out it looks exactly like VS Code. There's also an option to open Gitpod into your VS Code desktop version.

Everything works like in VS Code and thus you should be able to run anything using the same commands.

Gitpod has some [fantastic resources](https://www.gitpod.io/docs/introduction/getting-started) to get you started.

## Foundry Setup

Welcome to this handy guide on installing and operating Foundry, a versatile tool that will add a new level of command-line ease to your developer journey. Whether you're running Windows, Linux or MacOS, we've got you covered with instructions and tips. So sit back, grab a cup of coffee, and let's dive in.

## Prepping your Terminal

First things first. Before we dive into installing Foundry, make sure you have your terminal set up correctly.

If you are using Windows, you should see something like `WSL` or `Ubuntu`. Once you have your terminal environment ready, it’s time for some quick tips to help streamline your workflow.

### Keeping your Terminal Clutter-free

When commands pile up in your terminal, things can get a little overwhelming. Clear it up by simply typing `clear` and hitting `Enter`. Alternatively, use `Command K` if you're on a Mac or `Control K` if you're on Linux or Windows.

**Pro tip:** This is one of my favorite keyboard shortcuts that I use all the time.

### Understanding the Trash Can and the X

The trash can and the X buttons in your terminal perform distinct functions. Hitting `X` simply hides your terminal but retains all the previous lines of code. On the other hand, trashing it essentially deletes whatever is running in it. To open up a clean terminal, hit the trash can and then pull it back using `Toggle` or `Terminal > New Terminal`.

## Installing Foundry

With our terminal set and some tips up our sleeve, let's progress to installing Foundry. Navigate to the [Foundry website](https://book.getfoundry.sh/getting-started/installation) and from the installation tab, fetch the command to install Foundry.

The command would look something like this:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

Hit `Enter` after pasting this in your terminal.

**Note:** You must have Internet access for this to work as it's downloading Foundry from their official website.

## Verifying Your Installation

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

Now, here's something to remember: when you hit the trash can in the top right, it literally 'removes' the terminal. The X button, in contrast, simply hides it.

### Is Foundry Up Not Running?

Don't panic if this command doesn't run. You might have an issue with your path, and you might need to add Foundry to your path. In case you run into this issue, check lesson 6 of the GitHub repo associated with this course. If no debugging tips are available there, feel free to start a discussion on the course's GitHub repo. Before doing so, make sure to check if a similar discussion already exists.

Try typing `forge --version` into your terminal. Have you received an unwelcome output saying `Forge command found`? This implies that you have to rerun the `source` command that Foundry offered during installation.

Note: Most of the time the `bashrc` file gets loaded automatically. However, if this doesn't apply to your setup, the following lines can add the required command to the end of your `Bash profile`. This will ensure that your `bashrc` file loads by default.

```bash
cd ~
echo 'source /home/user/.bashrc' >> ~/.bash_profile
```

> this depends on your operating system, please check foundry docs to see detailed instructions.

## Wrapping Up

And there we have it! Congratulations on installing Foundry and prepping your terminal to work seamlessly with it. Remember, hitting snags during installation is normal, especially if you're new to this. Don't hesitate to engage with the course community via GitHub if you run into issues.

## VS Code setup

### Installing VS Code extensions

1. Open the Extensions view:

There are two ways to do this:

Click the Extensions icon in the Activity Bar on the left side of VS Code.

Use the shortcut Ctrl+Shift+X (Windows/Linux) or Cmd+Shift+X (Mac).

1. Browse or search for extensions:

The Extensions view displays featured extensions by default.

Use the search bar to find a specific extension by name.

1. Install the extension:

Once you've found the extension you want, click the "Install" button.
VS Code will handle the download and installation process.

**That's it! The extension should be ready to use within VS Code.**

### Integrating AI into our work

One of the best extensions that integrates AI in our development is GitHub Copilot

Although it's a premium service, its intuitive AI-powered code autocomplete feature could be a game-changer for you. Of course, you can choose to go with other AI extensions based on your preferences.

You can download GitHub Copilot [here](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot). More details and answers for your GitHub Copilot-related questions are available [here](https://github.com/features/copilot/?editor=vscode#faq).

### Other important VS Code Tips

**_Beware the white dot_**, if you see it, your work is not saved, which means your project won't behave the way you want it to behave.

`` CTRL(CMD) + `  `` opens/closes your terminal. It's the equivalent of pressing the `X` button on the top right part of your terminal.

The `trash can` button, on the left side of the `X` button destroys the terminal, make sure you always remember the difference between these two buttons.

Hooray! This concludes the setup part of this course. Now we get to the fun part, actually developing a project using solidity and foundry.

### More setup ...

Run the following commands in your terminal:

```Solidity
mkdir foundry-f23
cd foundry-f23
```

`mkdir` creates a directory or subdirectory.
`cd` changes the directory.

Moving forward, it's advisable to keep all your repositories in this folder. Thus, you'll always have a place to reference all your code.

## Create a new Foundry Project

Make sure we are in the folder we created in the previous lesson.

**Reminder**: We ran the following commands

```Solidity
mkdir foundry-f23
cd foundry-f23
```

Now type the following commands:

```Solidity
mkdir foundry-simple-storage-f23
cd foundry-simple-storage-f23
```

You can always make the `cd` command faster by pressing the `Tab` key after you type the first couple of letters from the destination name. `Tab` lets you autocomplete a lot of commands/paths.

If you type `code .` a new instance of VS Code will open, having the `foundry-simple-storage-f23` as the default path.

You can see the contents of this folder on the left sidebar. Try the following command:

```Solidity
touch randomFile.txt
```

This will create a `randomFile.txt`

If you want to delete it type:

```Solidity
rm randomFile.txt
```

The terminal is pretty slick when it comes to moving/opening/creating directories/files, changing paths and generally running things. I recommend going through [this tutorial](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview) if you want to learn how to move extra fast.

### Creating a New Project

The way you [create a new Foundry project](https://book.getfoundry.sh/projects/creating-a-new-project) is by running the `forge init` command. This will create a new Foundry project in your current working directory.

If you want Foundry to create the new project in a new folder type `forge init nameOfNewFolder`.

Keep in mind that by default `forge init` expects an empty folder. If your folder is not empty you must run `forge init --force .`

Be sure to configure your username and email if you encounter errors related to Git configuration.

```Solidity
git config --global user.email "yourEmail@provider.com"
git config --global user.name "yourUsername"
```

And that's it, your folder should look as follows:

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

More on these folders and files later.

Please right-click `src`, click on `New File` and name it `SimpleStorage.sol`. Copy the code available [here](https://github.com/Cyfrin/foundry-simple-storage-f23/blob/main/src/SimpleStorage.sol).

One last thing, please delete `Counter.s.sol`, `Counter.sol` and `Counter.t.sol`. These files are a set of basic smart contracts that Foundry provides as a default when you create a new Foundry project.

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

### More terminal wizardry

Throughout your solidity development/audit journey you will type a lot of terminal commands, every time to make a change that you want tested you'll probably have to rerun the `forge build` then maybe you test it with `forge test` or run a script with `forge script` and many more. Typing all these over and over again is inefficient and time-consuming. The better way is to use the `up` and `down` arrow keys. Type the following commands:

```Solidity
echo "I like Foundry"
echo "I love Cyfrin"
echo "Auditing is great"
```

Now press the `up` and `down` arrow keys to cycle through the 3 commands.

Ok, cool! We learned how to compile a contract, but how does one deploy a smart contract?

## Deploy a smart contract locally using Anvil

There are multiple ways and multiple places where you could deploy a smart contract.

While developing using the Foundry framework the easiest and most readily available place for deployment is Anvil.

Anvil is a local testnet node shipped with Foundry. You can use it for testing your contracts from frontends or for interacting over RPC.

To run Anvil you simply have to type `anvil` in the terminal.

<img src='./images/deploy-smart-contract-anvil/anvil.png' alt='anvil' />

You now have access to 10 test addresses funded with 10\_000 ETH each, with their associated private keys.

This testnet node always listens on `127.0.0.1:8545` this will be our `RPC_URL` parameter when we deploy smart contracts here. More on this later!

More info about Anvil is available [here](https://book.getfoundry.sh/reference/anvil/).

Please press `Ctrl/CMD + C` to close Anvil.

Anvil will be used throughout the course to deploy and test our smart contracts, but before that, let's quickly check an intermediary step.

### Ganache

_Ganache is a glaze, icing, sauce, or filling for pastries usually made by heating equal parts weight of cream and chopped chocolate, warming the cream first, then pouring it over the chocolate._

Wait, not that ganache! The other ganache:

Ganache is a personal blockchain for rapid Ethereum and Filecoin distributed application development. You can use Ganache across the entire development cycle; enabling you to develop, deploy, and test your dApps in a safe and deterministic environment.

Better!

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

We will teach you more about how to secure private keys in one of the next lessons.


Hacking private keys is one of the most important reasons people and projects lose absurd amounts. You don't even need to look that deep to find titles like this:

[The Ronin hack](https://www.halborn.com/blog/post/explained-the-ronin-hack-march-2022) - Social engineering of private keys

[Early Crypto Investor Bo Shen Says He Lost \$42 Million in Wallet Hack](https://www.bnnbloomberg.ca/early-crypto-investor-bo-shen-says-he-lost-42-million-in-wallet-hack-1.1850446)

[The \$477 million FTX hack](https://www.elliptic.co/blog/the-477-million-ftx-hack-following-the-blockchain-trail) where `The new CEO of FTX revealed that private keys allowing access to the firm’s crypto assets were stored in unencrypted form, and a former employee disclosed that over $150 million was stolen from Alameda Research, due to poor security. `&#x20;

Don't be like that! Maybe you are not holding millions, but what you hold is yours, don't let it become theirs!

In the following lessons, we'll learn how to access RPC URLs for free using Alchemy for any blockchain. We will also delve into exploring safer methodologies for dealing with private keys. Stay tuned!

# others
<!-- 
## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

-   **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
-   **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
-   **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
-   **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
``` -->
