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
