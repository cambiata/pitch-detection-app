# Pitch Detection App
An open source pitch detection app that uses Rust and WebAssembly

## Live Demo
[![Demo Page](./demo.png)](https://alesgenova.github.io/pitch-detection-app/)

## Components
### Core Pitch Detection Library
- Rust ([source](https://github.com/alesgenova/pitch-detection))

### Communication with web worker
- post-me ([source](https://github.com/alesgenova/post-me))

### WebAssembly Wrapper
- Rust / wasm-bindgen ([source](https://github.com/alesgenova/pitch-detection-app/tree/master/wasm))

### Pitch Visualization
- TypeScript, HTML5 Canvas, D3 ([source](https://github.com/alesgenova/pitch-detection-app/tree/master/display))

### Single Page App
- React ([source](https://github.com/alesgenova/pitch-detection-app/tree/master/client))

### Building

Versions used:
- Rust 1.96
- Node: v24.18.0

```bash
# Build wasm
# Prerequisite: cargo and wasm-pack
cd wasm
wasm-pack build --target web
```

NOTE: You might have to specify the Rust version in the Cargo.toml:
```bash
[package]
...
rust-version = "1.96"
```
and change the pitch-detection dependency to 3.0.0:

```bash
[dependencies]
... 
pitch-detection = "0.3.0"
```

Go on with building the wrapping js application:

```bash
# Build the visualization
cd ../display
npm install
npm run build

# Start the app
cd ../client
npm install
npm run start
```

NOTE: You might need yarn instead of npm to install the dependencies:
```bash
cd ../client
yarn
yarn start
```

Also, you might need to run the following on your command line:

```bash
# Source - https://stackoverflow.com/a/69699772
# Posted by Ajoy Karmakar, modified by community. See post 'Timeline' for change history
# Retrieved 2026-06-29, License - CC BY-SA 4.0

# unix, linux, mac
export NODE_OPTIONS=--openssl-legacy-provider

# windows command prompt
set NODE_OPTIONS=--openssl-legacy-provider

# windows power shell
$env:NODE_OPTIONS = "--openssl-legacy-provider"
```
