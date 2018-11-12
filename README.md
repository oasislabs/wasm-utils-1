# owasm-utils

Collection of WASM utilities used in Oasis and WASM contract development

[Documentation](https://docs.rs/crate/owasm-utils)

This crate is forked from [paritytech/wasm-utils](https://github.com/paritytech/wasm-utils).

We are big fans of the work [Parity](https://www.parity.io/) is doing to advance the state of Ethereum and smart contract development. In order to further experiment with new features including new opcodes and gas models, we have forked these repositories.

In the spirit of open-source, we intend to contribute bug fixes and new features upstream and will make our changes available to the community.


## Build tools for cargo

Easiest way to use is to install via `cargo install`:

```
cargo install owasm-utils-cli --bin wasm-build
```

## Symbols pruning (wasm-prune)

```
cargo install owasm-utils-cli --bin wasm-prune
wasm-prune <input_wasm_binary.wasm> <output_wasm_binary.wasm>
```

This will optimize WASM symbols tree to leave only those elements that are used by contract `call` function entry.

## Gas counter (wasm-gas)

For development puposes, raw WASM contract can be injected with gas counters (the same way as it done by Oasis runtime when running contracts)

```
cargo install owasm-utils-cli --bin wasm-gas
wasm-gas <input_wasm_binary.wasm> <output_wasm_binary.wasm>
```

## Externalization (wasm-ext)

Oasis WASM runtime provides some library functions that can be commonly found in libc. WASM binary size can be reduced and performance may be improved if these functions are used. This utility scans for invocations of the following functions inside the WASM binary:
- `_malloc`,
- `_free`,
- `_memcpy`,
- `_memset`,
- `_memmove`

And then substitutes them with invocations of the imported ones. Should be run before `wasm-opt` for better results.

```
cargo install owasm-utils-cli --bin wasm-ext
wasm-ext <input_wasm_binary.wasm> <output_wasm_binary.wasm>
```

## API

All executables use corresponding api methods of the root crate and can be combined in other build tools.

# License

`owasm-utils` is primarily distributed under the terms of both the MIT
license and the Apache License (Version 2.0), at your choice.

See LICENSE-APACHE, and LICENSE-MIT for details.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `owasm-utils` by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
