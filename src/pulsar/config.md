# Config

## Usage

TODO: Add this to `pulsar` CLI. <br/>
> There is an [issue](https://github.com/subspace/pulsar/issues/248) that asks for adding this feature so that a user can set config via CLI tool.

## Demystify

### Q. How is the config file created?

It is created by `$ pulsar init` command. Read [this](./init.md) for more.

And then the returned value is created in a toml Table i.e. BTreeMap. The config struct is defined as:

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/config.rs#L20-L26

/// structure of the config toml file
#[derive(Deserialize, Serialize, Debug)]
pub(crate) struct Config {
    pub(crate) chain: ChainConfig,
    pub(crate) farmer: FarmerConfig,
    pub(crate) node: NodeConfig,
}
```

### Q. What are the components of the config file?

Refer [this](./init.md#2-configuration-components) section of `init` command.

### Q. Could you explain the `advanced` settings for farmer and node?

Both the farmer and node configurations have placeholders for advanced settings (`AdvancedFarmerSettings` and `AdvancedNodeSettings`), which are set to default values during initialization. These settings allow for further customization of the farming and node operation.

For node, the `AdvancedNodeSettings` struct is defined as:

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/config.rs#L28-L35

/// Advanced Node Settings Wrapper for CLI
#[derive(Deserialize, Serialize, Clone, Debug, Default, PartialEq)]
pub(crate) struct AdvancedNodeSettings {
    #[serde(default, skip_serializing_if = "crate::utils::is_default")]
    pub(crate) enable_domains: bool,
    #[serde(default, flatten)]
    pub(crate) extra: toml::Table,
}
```

<details>

<summary><b>Code explanation:</b></summary>

When `AdvancedNodeSettings::default()` is called, it creates an instance of `AdvancedNodeSettings` with its fields set to their default values, as follows:

1. **`enable_domains`**: Since this field is of type `bool`, and there is no specific default value provided via an attribute like `#[derivative(Default(value = "..."))]`, it will default to `false`. The `bool` type in Rust defaults to `false` when the `Default` trait is implemented or derived without specifying otherwise.

2. **`extra`**: Similar to the previous case, the `extra` field is a `toml::Table` and is annotated with `#[serde(default, flatten)]`. The `#[serde(default)]` ensures that if the `extra` field is missing during deserialization, it will be set to its default value. For a `toml::Table`, the default is an empty table. The `flatten` attribute affects serialization and deserialization behavior but does not influence the default value.

So, calling `AdvancedNodeSettings::default()` will return an `AdvancedNodeSettings` instance where `enable_domains` is `false`, and `extra` is an empty `toml::Table`.

</details>

And then it is part of the `NodeConfig` struct:

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/config.rs#L37-L44

/// Node Options Wrapper for CLI
#[derive(Deserialize, Serialize, Clone, Debug)]
pub(crate) struct NodeConfig {
    pub(crate) directory: PathBuf,
    pub(crate) name: String,
    #[serde(default, skip_serializing_if = "crate::utils::is_default")]
    pub(crate) advanced: AdvancedNodeSettings,
}
```

---

For farmer, the `AdvancedFarmerSettings` struct is defined as:

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/config.rs#L109-L119

/// Advanced Farmer Settings Wrapper for CLI
#[derive(Deserialize, Serialize, Clone, Derivative, Debug, PartialEq)]
#[derivative(Default)]
pub(crate) struct AdvancedFarmerSettings {
    #[serde(default, skip_serializing_if = "crate::utils::is_default")]
    //TODO: change this back to 1GB when DSN is working properly
    #[derivative(Default(value = "subspace_sdk::ByteSize::gb(3)"))]
    pub(crate) cache_size: ByteSize,
    #[serde(default, flatten)]
    pub(crate) extra: toml::Table,
}
```

<details>

<summary><b>Code explanation:</b></summary>

When `AdvancedFarmerSettings::default()` is called, it returns an instance of `AdvancedFarmerSettings` with its fields set to default values as specified in its implementation. Here's what happens for each field based on the provided definition:

1. **`cache_size`**: This field is set to a default value using the `#[derivative(Default(value = "..."))]` attribute. Specifically, it is set to `subspace_sdk::ByteSize::gb(3)`, which means the default cache size is 3 gigabytes. This is explicitly defined in the attribute and overrides the standard `Default` trait behavior for this field.

2. **`extra`**: The `extra` field is a `toml::Table`, and it's annotated with `#[serde(default, flatten)]`. The `#[serde(default)]` part ensures that if the `extra` field is missing during deserialization, it will be set to its default value, which, for a `toml::Table`, is an empty table. The `flatten` attribute is used for serialization/deserialization purposes and does not affect the default value.

In summary, calling `AdvancedFarmerSettings::default()` will create an `AdvancedFarmerSettings` instance where `cache_size` is set to 3GB, and `extra` is an empty `toml::Table`.

</details>

And then it is part of the `FarmerConfig` struct:

```rust
// Source code: https://github.com/subspace/pulsar/blob/d55065a9991caac27286c14b9e5977ca3025fa3d/src/config.rs#L121-L129

/// Farmer Options Wrapper for CLI
#[derive(Deserialize, Serialize, Clone, Debug)]
pub(crate) struct FarmerConfig {
    pub(crate) reward_address: PublicKey,
    pub(crate) farm_directory: PathBuf,
    pub(crate) farm_size: ByteSize,
    #[serde(default, skip_serializing_if = "crate::utils::is_default")]
    pub(crate) advanced: AdvancedFarmerSettings,
}
```
