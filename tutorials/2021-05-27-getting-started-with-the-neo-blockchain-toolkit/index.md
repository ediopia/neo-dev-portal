---
title: 'Getting Started with the Neo Blockchain Toolkit'
description: "The Neo Blockchain Toolkit is a one-stop-shop for creating and preparing smart contracts for production, seamlessly integrated with VS Code"
author: ngdenterprise.com
tags: [ "NEO BLOCKCHAIN TOOLKIT", "C#"]
skill: beginner
image: ./assets/cover.png
sidebar: true
---

# Getting Started with the Neo Blockchain Toolkit



## Quick Start 1: Getting Started with the Neo Blockchain Toolkit


<video controls width="100%" height="480">
      <source src="https://ngdenterprise.com/neo-tutorials/static/quick-start-files/quick-start-1.mp4" type="video/mp4" />
</video>

Notes:
------

The .NET SDK can be downloaded from:  
[https://dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)

Visual Studio Code can be downloaded from:  
[https://code.visualstudio.com/](https://code.visualstudio.com/)

This is the URL to the official Neo Blockchain Toolkit extension for Visual Studio Code:  
[https://marketplace.visualstudio.com/items?itemName=ngd-seattle.neo-blockchain-toolkit](https://marketplace.visualstudio.com/items?itemName=ngd-seattle.neo-blockchain-toolkit)

Platform specific errata:

_MacOS:_ Running Neo Express on MacOS requires installing rocksdb via [Homebrew](https://brew.sh/):  
`$ brew install rocksdb`

_Linux:_ Running Neo Express on Linux requires installing libsnappy and libc6. For example, on systems using the apt package manager:  
`$ sudo apt install libsnappy-dev libc6-dev -y`

Commands used in this video:

_Checking for .NET SDK installation:_  
`$ dotnet --version`  
(Check for a value greater than 5.)

---

## Quick Start 2: Working with the Private Net
<video controls width="100%" height="480">
      <source src="https://ngdenterprise.com/neo-tutorials/static/quick-start-files/quick-start-2.mp4" type="video/mp4" />
</video>

---

## Quick Start 3: Working with Wallets and Assets

<video controls width="100%" height="480">
      <source src="https://ngdenterprise.com/neo-tutorials/static/quick-start-files/quick-start-3.mp4" type="video/mp4" />
</video>

---

## Quick Start 4: Building your first Smart Contract

<video controls width="100%" height="480">
      <source src="https://ngdenterprise.com/neo-tutorials/static/quick-start-files/quick-start-4.mp4" type="video/mp4" />
</video>

Notes:
------

This is the URL to the official C# extension for Visual Studio Code:  
[https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)

Commands used in this video:

_Installing the Neo C# compiler:_  
`$ dotnet tool install -g neo.compiler.csharp --version 3.0.0-rc2`  
(Please note that the tool name has changed since the video was recorded. ALso note that the --version parameter 

---

## Quick Start 5: Debugging your Smart Contract

<video controls width="100%" height="480">
      <source src="https://ngdenterprise.com/neo-tutorials/static/quick-start-files/quick-start-5.mp4" type="video/mp4" />
</video>

Notes:
------
The launch.json schema for debugging Neo Smart Contracts is documented here:  
[https://github.com/neo-project/neo-debugger/blob/master/docs/debug-config-reference.md](https://github.com/neo-project/neo-debugger/blob/master/docs/debug-config-reference.md)