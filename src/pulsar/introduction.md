# Pulsar

There is a CLI tool called `pulsar` which abstracts the node & farming process.
It's a CLI tool that can be mainly used to farm and has a node running in the background.

The tool is a versatile component of the Subspace network, a blockchain platform designed for decentralized storage and consensus. It serves as a farming and node management utility, facilitating users in contributing disk space for network consensus while simultaneously participating in the network's operations.

Key functionalities of the Pulsar tool include:

- <u>Initialization</u>: Setting up the user environment, including configuration of node identity, storage paths, and network settings.
- <u>Farming Commands</u>: Managing the farming process, where users allocate disk space (referred to as plots) to support the network's consensus mechanism, earning rewards in the process.
- <u>Node Management</u>: Overseeing the operational aspects of the node, ensuring smooth participation in the network activities.
- <u>Configuration Management</u>: Providing users with the ability to configure and customize their farming and node operations through a TOML configuration file.
- <u>Wipe Functionality</u>: Enabling users to cleanly reset their environment by wiping node data, farmer data, summary information, and configurations, offering a fresh start when needed.

For more, please refer to the [pulsar](https://github.com/subspace/pulsar) repository.

Now, let's understand from the code perspective now starting with the [`init` command](./init.md). Each chapter has a 'Demystify' section that breaks down the code and explains the functionality in detail.
