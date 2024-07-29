# zfetch

![](vhs/zfetch.gif)

zfetch is a command line tool for managing NixOS configuration.

> :warning: **Work in Progress**: This project is currently under development. Some features may not be complete and may change in the future.
## Installation

To install zfetch, you can clone the repository and compile the source code:

```sh
git clone https://github.com/alvaro17f/zfetch.git
cd zfetch
zig build run
```

then move the binary to a directory in your PATH:

```sh
sudo mv zig-out/bin/zfetch <PATH>
```

### NixOS

#### Run
To run zfetch, you can use the following command:

```sh
nix run github:alvaro17f/zfetch#target.x86_64-linux-musl
```

#### Flake
Add zfetch to your flake.nix file:

```nix
{
    inputs = {
        zfetch.url = "github:alvaro17f/zfetch";
    };
}
```

then include it in your system configuration:

```nix
{ inputs, pkgs, ... }:
{
    home.packages = [
        inputs.zfetch.packages.${pkgs.system}.default
    ];
}
```

## Usage
```sh
 ***************************************************
 zfetch - A simple CLI tool to update your nixos system
 ***************************************************
 -r : set repo path (default is $HOME/.dotfiles)
 -n : set hostname (default is OS hostname)
 -k : set generations to keep (default is 10)
 -u : set update to true (default is false)
 -d : set diff to true (default is false)
 -h, help : Display this help message
 -v, version : Display the current version
```


## License
zfetch is distributed under the MIT license. See the LICENSE file for more information.

