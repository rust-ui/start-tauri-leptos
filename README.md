# Test Tauri App

This uses leptos ssr embedded as external binary (sidecar) on tauri.

## Getting Started


1. Generate Tauri Icons

Note: Without Icons you will have issue with running cargo tauri `{dev | build}`

```sh
# assuming your are on the workspace root directory
cd src-tauri
cargo tauri icon /path/to/icon.png
```

2. Run Build Script

Note: this is required at least to be run once since during tauri compilation it would look for the `server` binary listed on your [tauri.conf.json](./src-tauri/tauri-conf.json)

```json
 "externalBin": [
      "../target/release/server"
    ]
```

During the First Run of `cargo tauri dev` , your `target/release/server` is not found

but if your running `cargo tauri build` that would be generated as the script `build-binaries.sh` would be run


- Linux / MacOS

```sh
# if the script isnt executable yet then run
chmod +x ./build-binaries.sh
# Run the script
./build-binaries.sh
```

- Windows

```powershell
.\build-binaries.ps1
```

3. Development

```sh
cargo tauri dev
```

4. Production Build

```sh
cargo tauri build
```


## Project Structure

```sh
- app # where you add your UI, components and routes
- server # Leptos SSR (sidecar)
- src-tauri # add all your tauri good stuff here and commands
- style # tailwind stuff
```

If you need to run sidecar app process (LEPTOS SSR SERVER) on different port please check [sidecar.rs](./src-tauri/src/sidecar.rs) and update `leptos_address` and `leptos_reload_port`

