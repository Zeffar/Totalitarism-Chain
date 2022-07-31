# Totalitarism Chain Description

A ready for hacking FRAME-based Substrate node 

## Getting Started

This project contains some configuration files

### Makefile

This project is using a Makefile for easier execution. (for help check https://www.gnu.org/software/make/manual/make.html)
run these:

1. `make init` -  configure the Rust toolchain
1. `make run` - build and launch this project (Dev mode).

### Build

To build the node without launching it run this command:

```sh
make build
```

### Embedded Docs

Once the project has been built, run the following command to browse through parameters:

```sh
./target/release/node-template -h
```

### Multi-Node Local Testnet

For running the multi-node consensus algorithm, we have refered to this substrate tutorial:
https://substrate.dev/docs/en/tutorials/start-a-private-network

## Structure

A Substrate project such as this consists of a number of components that are spread across a few
directories.

After the node has been [built](#build), refer to the embedded documentation to learn more about the
capabilities and configuration parameters that it exposes:

```shell
./target/release/node-template --help
```

### Pallets

The runtime in this project is constructed using many FRAME pallets that ship with the
core Substrate repository and a
template pallet that is defined in the `pallets` directory.

A FRAME pallet is compromised of a number of blockchain primitives:

-   Storage: FRAME defines a rich set of powerful
    storage abstractions that makes
    it easy to use Substrate's efficient key-value database to manage the evolving state of a
    blockchain.
-   Dispatchables: FRAME pallets define special types of functions that can be invoked (dispatched)
    from outside of the runtime in order to update its state.
-   Events: Substrate uses events to
    notify users of important changes in the runtime.
-   Errors: When a dispatchable fails, it returns an error.
-   Trait: The `Trait` configuration interface is used to define the types and parameters upon which
    a FRAME pallet depends.

### Run in Docker


Run the following command to start a single node development chain.

```bash
./scripts/docker_run.sh
```

This command will firstly compile our code, and then start a local dev network. A few useful ones are as follow.

```bash
# Run Substrate node without re-compiling
./scripts/docker_run.sh ./target/release/node-template --dev --ws-external

# Purge the local dev chain
./scripts/docker_run.sh ./target/release/node-template purge-chain --dev

# Check whether the code is compilable
./scripts/docker_run.sh cargo check
```
