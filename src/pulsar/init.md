# init

This command is designed to initialize the tool by setting up the necessary configuration based on user input.

Here are the key functionalities of the `init` command as derived from the source code:

## Usage

```bash
$ pulsar init                                                                 ⏎

 ____             __                                              __  __          __                               __
/\  _`\          /\ \                                            /\ \/\ \        /\ \__                           /\ \
\ \,\L\_\  __  __\ \ \____    ____  _____      __      ___     __\ \ `\\ \     __\ \ ,_\  __  __  __    ___   _ __\ \ \/'\
 \/_\__ \ /\ \/\ \\ \ '__`\  /',__\/\ '__`\  /'__`\   /'___\ /'__`\ \ , ` \  /'__`\ \ \/ /\ \/\ \/\ \  / __`\/\`'__\ \ , <
   /\ \L\ \ \ \_\ \\ \ \L\ \/\__, `\ \ \L\ \/\ \L\.\_/\ \__//\  __/\ \ \`\ \/\  __/\ \ \_\ \ \_/ \_/ \/\ \L\ \ \ \/ \ \ \\`\
   \ `\____\ \____/ \ \_,__/\/\____/\ \ ,__/\ \__/.\_\ \____\ \____\\ \_\ \_\ \____\\ \__\\ \___x___/'\ \____/\ \_\  \ \_\ \_\
    \/_____/\/___/   \/___/  \/___/  \ \ \/  \/__/\/_/\/____/\/____/ \/_/\/_/\/____/ \/__/ \/__//__/   \/___/  \/_/   \/_/\/_/
                                      \ \_\
                                       \/_/

version: 0.7.4

Configuration creation process has started...
Do you have an existing farmer/reward address? [y/n]: n
Do you want to create a new farmer/reward key? [y/n]: y
IMPORTANT NOTICE: The mnemonic displayed below is crucial to regain access to your account in case you forget your credentials. It's highly recommended to store it in a secure and retrievable location. Failure to do so may result in permanent loss of access to your account.

Please press 'Enter' after you've securely stored the mnemonic. Once you press 'Enter', the mnemonic will no longer be visible in this interface for security reasons.

Here is your mnemonic:
lawn winter clever noodle ready soon plastic clerk brave glad betray mutual

...redacted...
Enter the 5th word in the mnemonic: ready
Enter the 6th word in the mnemonic: soon
Enter the 3th word in the mnemonic: clever
Your new public key is: 5ESKTcWN12uXC2rysNyvteaB2AYKZapKFKN6yu9zSKV9Mtos
Enter your node name to be identified on the network(defaults to `abhi3700`, press enter to use the default): 
Specify a path for storing farm files (press enter to use the default: `"/Users/abhi3700/Library/Application Support/pulsar/farms"`): 
Specify a path for storing node files (press enter to use the default: `"/Users/abhi3700/Library/Application Support/pulsar/node"`): 
Specify a farm size (defaults to `2.0 GB`, press enter to use the default): 
Specify the chain to farm. Available options are: [Gemini3g, Dev, DevNet]. 
 Defaults to `Gemini3g`, press enter to use the default:
Configuration has been generated at /Users/abhi3700/Library/Application Support/pulsar
Ready for lift off! Run the follow command to begin:
`"pulsar" farm`
```

This command creates a `settings.toml` file in the appropriate directory based on system OS.

Let's view the content of `settings.toml` on macOS. Go to `~/Library/Application Support/pulsar`, then:

```bash
$ cat settings.toml 
chain = "Gemini3g"

[farmer]
reward_address = "62c1ada04c4363711be2ea7cc2f106735cb6007dac06317cca7da07b4650d948"
farm_directory = "/Users/abhi3700/Library/Application Support/pulsar/farms"
farm_size = "2.0 GB"

[node]
directory = "/Users/abhi3700/Library/Application Support/pulsar/node"
name = "abhi3700"
```

## Demystify

### Q. How is the pulsar init happens?

#### A. Main Functionality

1. Create `setting.toml` file in respective directories as per the system OS. Here is the relevant code snippet:

```rust
/// Creates a config file at the location
/// - **Linux:** `$HOME/.config/pulsar/settings.toml`.
/// - **macOS:** `$HOME/Library/Application Support/pulsar/settings.toml`.
/// - **Windows:** `{FOLDERID_RoamingAppData}/pulsar/settings.toml`.
pub(crate) fn create_config() -> Result<(File, PathBuf)> {
    let config_path =
        dirs::config_dir().expect("couldn't get the default config directory!").join("pulsar");

    if let Err(err) = create_dir_all(&config_path) {
        let config_path = config_path.to_str().expect("couldn't get pulsar config path!");
        return Err(err).wrap_err(format!("could not create the directory: `{config_path}`"));
    }

    let file = File::create(config_path.join("settings.toml"))?;

    Ok((file, config_path))
}
```

2. **ASCII Art and Version Display**: [prints a cool ASCII art](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/utils.rs#L26-L38) followed by the [version of the tool](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/utils.rs#L40-L44) to the console.

3. **Configuration Creation**: prompts the user for various inputs to create a configuration file. This process includes:

   - [Checking for an existing farmer/reward address](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L49-L55) and offering the option to [generate a new one if none exists](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L128-L200).
   - Prompting for a node name, which will be used to identify the node on the network. The default option is the user's system username, except for 'root'. [Code](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L59-L68)
   - Asking for directories to store farm and node files, with default suggestions provided. [Code](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L70-L89)
   - Requesting the desired farm size, with a default value defined by `DEFAULT_FARM_SIZE`. [Code](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L91-L99)
   - Selecting the chain to farm on from available options, with a default chain pre-selected. Defaults to the latest i.e. Gemini-3g (at the time of writing). [Code](https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L101-L111)

4. **Configuration File Creation**: Once the user has provided all the required inputs, the configuration file is created and written to the location specified in the first step. The file is named `settings.toml` and contains the configuration in the [TOML](https://toml.io/en/) format. Here is the code snippet inside `init()` function:

```rust
fn init() {
    // ...
    config_file
        .write_all(toml::to_string_pretty(&config).wrap_err("Failed to write config")?.as_ref())
        .wrap_err("Failed to write config")?;

    // ...
}
```

5. **Display `settings.toml` file path**: After successfully writing the configuration, the code prints out the file's location using `config_path.display()`. This informs the user where the configuration file is saved on their filesystem.

6. Run the command

#### B. Configuration Components

The configuration file generated by the `init` command consists of several components, including:

- **Farmer Config**: Contains settings related to the farming process, such as the farm size, directory, and the reward address.
  - Here, the default values for advanced farmer settings are **`cache_size`: 3 GB (initially, later on, can be set to 1 GB when DSN is working properly), `toml table`: empty table**.

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L113-L118
let farmer_config = FarmerConfig {
    farm_size,
    farm_directory,
    reward_address,
    advanced: AdvancedFarmerSettings::default(),
};
```

- **Node Config**: Includes the node's name and directory, along with advanced settings (which are set to their defaults in the initialization process).
  - Here, the default values for advanced node settings are **`enable_domains`: false, `toml table`: empty table**.

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L119-L123
let node_config = NodeConfig {
    name: node_name,
    directory: node_directory,
    advanced: AdvancedNodeSettings::default(),
};
```

- **Chain Config**: Specifies the blockchain network that the node will participate in.

---

Lastly, returned by `get_config_from_user_inputs()` function, which is then used in the `init()` function to set the config into a toml file.

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/commands/init.rs#L125
fn get_config_from_user_inputs() {
    // ...
    Ok(Config { farmer: farmer_config, node: node_config, chain })
}
```

### Q. How does the "Reward Address Generation" process happens?

If a user opts to generate a new farmer/reward address, the command will create a new key pair and display the mnemonic. It includes a security notice urging the user to securely store the mnemonic. The public key of the newly generated key pair is then presented as the farmer/reward address.

The generated configuration is written to a TOML file, and the location of this file is displayed to the user upon successful completion. The command also advises the user on the next steps to start using the tool.
