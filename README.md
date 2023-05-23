# git-favorite-branch

Quickly manage git branches during intensive multi-tasking work environments

## Usage

You can always run `gfb <SUBCOMMAND> -h` to get the latest usage.

```
Tiny CLI for enforcing branching name strategy across multiple repositories

Usage: gfb <COMMAND>

Commands:
  add      Add current branch to favorites
  use      Switch to a different branch
  del      Remove favorite branch
  del-all  Delete all favorite branches
  branch   Print Branch Name
  new      Create a new branch that is named with a value for a given key
  ls       List all favorite branches
  help     Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version

```

## Install

### Build Targets

While building the distribution, we leverage GH Actions to build on multiple OS. Here are all of the available build targets. **Replace `<target_string>` keyword with the target that best suites your operating system**

- `macOS_latest`
- `ubuntu_latest`

### Brand new install

All releases will be posted on the github repo. To install the cli for the first time run the following command.

```bash
export GFB_BUILD_TARGET=<target_string>; # Example export GFB_BUILD_TARGET="ubuntu_latest"
export GFB_VERSION=<version_string>; # Example export GFB_VERSION="v0.3.0"
curl https://raw.githubusercontent.com/VeprUA/git-favorite-branch/main/bin/install.sh | sh -s $GFB_VERSION $GFB_BUILD_TARGET
```

You are also more than welcome and download the binary zip from the release page. Just make sure to put it in the `/usr/local/revent-studio/gfb-v0.3.0/` directory. That way an update can be done cleanly.

Here is a helper script once you download your zip:

```bash
export GFB_BUILD_TARGET=<target_string>; # Example export GFB_BUILD_TARGET="ubuntu_latest"
export GFB_VERSION=<version_string>; # Example export GFB_VERSION="v0.3.0"

# Unzip and give execute permission
unzip gfb-$GFB_BUILD_TARGET.zip
chmod +x gfb-$GFB_BUILD_TARGET/gfb

# Create an install directory
sudo mkdir -p /usr/local/revent-studio/gfb-$GFB_VERSION

# Move the binary to the install directory
sudo mv gfb-$GFB_BUILD_TARGET/gfb /usr/local/revent-studio/gfb-$GFB_VERSION/gfb

# Create a symlink in the bin directroy
sudo ln -s /usr/local/revent-studio/gfb-$GFB_VERSION/gfb /usr/local/bin/gfb

```

Similar directions are used in the `bin/install.sh` file. You can always use that as a reference.

### Already using gfb

It is very simple to update the current binary. You don't need to provide a build target as that is baked in during the build process.

```bash
 gfb install
```

## Uninstall

You can always remove the cli from your machine by running the uninstall command in the `/bin` directory.

```bash
curl https://raw.githubusercontent.com/VeprUA/git-favorite-branch/main/bin/uninstall.sh | sh
```

## Build

Currenty we don't have a build avaialbe for multiple OS, so you will need to clone the repo and build it your self. No worries here is the guide to get it working on your machine.

**Requirements**

- Rust (latest)

Installation Instructions

1. Clone this repo

```bash
git clone git@github.com:VeprUA/git-favorite-branch.git
```

2. Build

```bash
export BUILD_TARGET="<build_target>"; cargo build
```

3. With the help of cargo make your executable visible to your environment

```bash
cargo install --path .
```

4. Run the executable

```bash
gfb
```
