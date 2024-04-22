# Apko Plugin

[![ci](https://github.com/fluentci-io/apko-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/apko-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [apko](https://github.com/chainguard-dev/apko).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm apko setup
```

## Functions

| Name   | Description                                |
| ------ | ------------------------------------------ |
| setup  | Installs a specific version of apko.       |
| build  |  Build an image from a YAML configuration file |
| build_minirootfs |  Build a minirootfs image from a YAML configuration file |
| login | Log in to a registry |
| publish | Build and publish an image |


## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.1.9"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/apko@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: apko
    args: |
      setup
    working-directory: example
- name: Show apko version
  run: |
    type apko
    apko version
```
