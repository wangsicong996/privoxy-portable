# Portable Privoxy Builder

This repository automatically builds portable versions of Privoxy for macOS and Linux using GitHub Actions.

The Privoxy configuration is modified to listen on `0.0.0.0:8118`, allowing devices on your local network to use it as a proxy.

## Downloads

You can download the latest portable versions from the **Actions** tab of this repository:
1. Go to the [Actions tab](https://github.com/[your-github-username]/[your-repo-name]/actions). (Replace `[your-github-username]/[your-repo-name]` with the actual path).
2. Click on the latest successful workflow run for the 'Build Portable Privoxy' workflow.
3. Under the "Artifacts" section, you will find:
    - `privoxy-portable-macos-latest`: A DMG file for macOS.
    - `privoxy-portable-ubuntu-latest`: A `.tar.gz` file for Linux.

## How to Use

### macOS (DMG)

1.  Download `privoxy-portable-macos-latest.dmg`.
2.  Open the DMG file.
3.  Drag the `Privoxy` application (or folder containing `privoxy` and `default.config`) to your Applications folder or any other location.
4.  Run Privoxy. It will use the included `default.config`.
    (Note: Depending on how the DMG is structured by the build, you might need to navigate into a folder within the DMG and run the `privoxy` executable from a terminal, or it might be a more complete app bundle if we enhance the macOS packaging later. For now, it will likely be the `privoxy` executable and `default.config`.)

### Linux (Tarball)

1.  Download `privoxy-portable-ubuntu-latest.tar.gz`.
2.  Extract the archive: `tar -xzf privoxy-portable-ubuntu-latest.tar.gz`
3.  This will create a directory (e.g., `privoxy-package`). Navigate into it: `cd privoxy-package`
4.  Run the launch script: `./start-privoxy.sh`
    This script starts Privoxy using the included `default.config` file.

## Configuration

The included `default.config` file has the `listen-address` set to `0.0.0.0:8118`. This means Privoxy will accept connections from any IP address on your local network.

**Security Note:** Be aware that allowing connections from `0.0.0.0` makes Privoxy accessible to any device on your network. Ensure your network is secure. If you only need to access Privoxy from the machine it's running on, you can change the `listen-address` back to `127.0.0.1:8118` in the `default.config` file.

## Building Locally (Optional)

If you want to build Privoxy locally using the same steps as the GitHub Actions workflow:
1. Clone this repository.
2. Ensure you have the necessary build dependencies installed for your OS (see `.github/workflows/build.yml` for details: `autoconf`, `automake`, `pcre` for macOS; `autoconf`, `automake`, `libpcre3-dev` for Linux).
3. Follow the compilation, configuration modification, and packaging steps outlined in the `.github/workflows/build.yml` file.
