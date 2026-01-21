# Soroban Hello World Contract

Minimal Soroban smart contract that returns a friendly greeting. This repository is structured as a Rust workspace with a single contract crate under `contracts/hello-world`.

## Features

- Simple `hello` method returning `"Hello"` and a provided name.
- Unit tests using `soroban_sdk`.
- Ready for local build and Testnet deployment.

## Prerequisites

- Rust (stable) with `cargo`
- Soroban CLI (`stellar`)
- Target: `wasm32v1-none`

Install the WASM target once:

```bash
rustup target add wasm32v1-none
```

## Build

From the repository root:

```bash
stellar contract build --package hello-world
```

The compiled WASM is placed at:

```text
contracts/hello-world/target/wasm32v1-none/release/hello_world.wasm
```

## Test

```bash
cargo test -p hello-world
```

## Deploy (Testnet)

```bash
stellar keys generate alice --network testnet --fund
stellar contract deploy \
	--wasm contracts/hello-world/target/wasm32v1-none/release/hello_world.wasm \
	--source-account alice \
	--network testnet \
	--alias hello_world
```

Deployed contract (Testnet):
https://lab.stellar.org/r/testnet/contract/CDHTOWGJHC77BFNHQIKTD64X5MWAJZL6PWENIPQAXH5O3CDKMIA4AH7N

## Project Structure

```text
.
├── contracts
│   └── hello-world
│       ├── src
│       │   ├── lib.rs
│       │   └── test.rs
│       └── Cargo.toml
├── Cargo.toml
└── README.md
```

## License

MIT (or your preferred license).
