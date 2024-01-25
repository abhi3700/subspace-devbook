# wipe

This command clears various components of the Pulsar setup. This can include the farmer (along with the farms/plots), node, summary, and configuration files.

## Usage

This is how the output looks like when using `wipe` command just after either

- `$ pulsar init` or,
- `$ pulsar init` -> `$ pulsar farm` (1 or more times) i.e. before/after node syncing is complete.

```bash
❯ pulsar wipe
Do you want to wipe farmer (delete farm)? [y/n]: y
Do you want to wipe node? [y/n]: y
Do you want to wipe summary? [y/n]: y
Do you want to wipe config? [y/n]: y
wiping node...
wiping farmer...
Skipping wiping summary, could not find the file...
Skipping wiping config, could not find the file...
Wipe finished!
```

---

Let's say you haven't run `$ pulsar init` and you want to wipe the config and summary files. Then, it won't be able to read the config file.

```bash
❯ pulsar wipe
Do you want to wipe farmer (delete farm)? [y/n]: y
Do you want to wipe node? [y/n]: y
Do you want to wipe summary? [y/n]: y
Do you want to wipe config? [y/n]: y
wiping node...
wiping farmer...
could not read your config. Wipe will still continue... 
However, if you have set a custom location for your plots, you will need to manually delete your plots!
Skipping wiping summary, could not find the file...
Skipping wiping config, could not find the file...
Wipe finished!
```

> NOTE:
>
> - In the second case, the config file could not be read as not set.
> - It deletes the directories:
>   - node: `/Users/abhi3700/Library/Application Support/pulsar/node`
>   - farm: `/Users/abhi3700/Library/Application Support/pulsar/farms`
> - It doesn't delete the `.subspaceFarmer` file which acts as the single farmer instance indicator.

## Demystify
