## Install NixOS

There are several ways to install NixOS. You can choose between a virtual machine or installing on dedicated hardware. Installing NixOS in a virtual machine is a great way to try it out, and the reproducibility of Nix means that we can easily copy a working configuration from our VM to dedicated hardware later on. We will cover how to install the NixOS image in a VM using VirtualBox, but if you are following along with dedicated hardware, the rest of the guide is essentially the same.

### VirtualBox

Download the ISO file of your choice from the [official source](https://nixos.org/download). We will use the recommended GNOME version, but it makes no difference if you choose Plasma instead.

You can follow this [guide](https://itsfoss.com/install-nixos-vm/#dont-reboot-but-turn-off-the-vm) on how to install NixOS in a VirtualBox VM. Below is a summary of the steps:

- Open VirtualBox
- Click on `New` in the menu bar
- Name your VM
- Choose the ISO image you've just downloaded
- Select `Linux` as the type of ISO
- Choose `Other Linux (64-bit)` for version
- Click `next`
- (Recommended) Choose at least 4GB of RAM
- (Recommended) Choose at least 2-4 processor cores
- (Recommended) Choose at least 30GB for this install
- If everything looks good, click `Finish` and VirtualBox will create a NixOS virtual machine for you.

- Go through the graphical installer with your preferred settings.
- At the `Install` stage, it might appear to be stuck at 46%. Don't worry, let the installer do its thing and check back later.

- At the last step upon completing the installer, **do not reboot** but turn off the VM. Otherwise it will load the installer again!
- To power off the VM, select the `Close` option from the **File menu** and select `Power off the machine`

- Change the boot order in VirtualBox
  - To change the boot order in the NixOS VM, open the settings for that VM
  - In settings, select `System` and there you will find the boot order
  - Here, select `Hard Disk` and use the **up arrow** icon next to the options to make it the first boot option
  - Press `OK` to save the changes you'e made.
  - Alternatively, you can remove the ISO image that we added to start the installation

## First look at NixOS

First let's take a look around our newly installed environment and familiarise ourselves with it.

Open up a console and navigate to the `/etc/nixos` directory and see what's there

```bash
cd /etc/nixos
ls
```

You should see a file called `configuration.nix` and a `hardware-configuration.nix` file. The `hardware-configuration.nix` is tailored to your specific system is probably not something we want to be messing with, so we will mostly ignore it in the rest of this guide.

On the other hand, `configuration.nix` defines our system thus far, let's take a look at the auto-generated `configuration.nix`.

```bash
sudo nano configuration.nix
```

Here we can see some things that we can change, like the hostname.

We also see that packages installed are defined in two places. One for the user, and the other for system-wide packages.

```nix
# configuration.nix

# user packages
users.users.username = {
    isNormalUser = true;
    description = "main user";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
        # thunderbird
    ];
};

# system-wide packages
environment.systemPackages = with pkgs; [
    vim
    wget
    git
];
```

Note: change `username` to your username instead.

Hint: to find packages to install, a good resource is [mynixos.com](https://mynixos.com)

As an example, let's add `vim`, `wget` and `git`, to the system packages.

```nix
# configuration.nix

environment.systemPackages = with pkgs; [
    vim
    wget
    git
];
```

Once we have some packages in our user packages block and/or the system packages block, we can synchronise the system state with the state of the configuration file.

To do this, save the file

and then run the following command

```bash
sudo nixos-rebuild switch
```

The `nixos-rebuild` part tells NixOS to rebuild with our new packages installed. The `switch` part tells NixOS to "switch" to the newly built system.

You might notice that there are a bunch of references in the command output to something called `/nix/store`. This is basically where all the programmes that you have installed will live.

Try editing a file with `vim` and it should now be installed.

## Channels -> Flakes

So far we have been using channels to install our packages. But most people in the Nix community are using something called **flakes**.

Flakes have a few advantages that make things a lot easier.

Channels and flakes both manage the packages installed on a system. The difference is that in the flake approach, there is a file called `flake.lock` that keeps track of the exact versions of all packages explicitly. This means that if we keep track of `flake.lock` using a version manager like git, then we can have a literal time machine of what goes on in the system. In case something breaks on the system, we can revert to an earlier version at a moment's notice, simply by reverting our git repo to that earlier version.

So flakes are very cool. The first step to start using flakes is to enable the ability to use flakes in our `configuration.nix` file.

```bash
sudo nano configuration.nix
```

Go to the bottom of the file and before the closing curly brace, add this following line to your configuration.

```nix
# configuration.nix

nix.settings.experimental-features = [ "nix-command" "flakes" ];
```

Save your configuration file and rebuild again with `sudo nixos-rebuild switch`.

## Using flakes

We prefer to create new directory in the user's home directory called `.dotfiles` but you can choose to call it whatever you want.

```bash
mkdir ~/.dotfiles
cd ~/.dotfiles
```

The first thing we are going to do before we initialise our flake is to copy the `configuration.nix` and `hardware-configuration.nix` from `/etc/nixos`.

```bash
cp /etc/nixos/configuration.nix .
cp /etc/nixos/hardware-configuration.nix .
```

Then we will create our `flake.nix` file using our favourite text editor.

```bash
vim flake.nix
```

A basic `flake.nix` file has three parts. The description, inputs, and outputs.

```nix
# flake.nix

{
    description = "my nix flake";

    inputs = {};

    outputs = {};
}
```

The inputs contain some git repos, for example nixpkgs or nix-bitcoin.

The outputs contain your built and working system configuration.

### Inputs

To add nixpkgs as an input to our flake, we just need to tell Nix the url of where to find it.

```nix
# flake.nix

{
    #...

    inputs = {
        nixpkgs = {
            url = "github:NixOS/nixpkgs/nixos-unstable";
        };
    };

    # ...
}
```

There is also a shorthand way to rewrite the above, which gives us functionally the same result. Since nixpkgs is a special repo in NixOS, we don't need to specify github in front of it.

```nix
# flake.nix

{
    # ...

    inputs = {
        nixpkgs.url = "nixpkgs/nixos-unstable";
    };

    # ...
}
```

### Outputs

Now that we have added some inputs, we can make use of them in our outputs.

Let's create our NixOS configuration in our outputs using the inputs we've added earlier.

```nix
# flake.nix

{
    # ...

    outputs = { self, nixpkgs, ... }:
    let
        lib = nixpkgs.lib;
    in {
        nixosConfigurations = {
            hostname = lib.nixosSystem {
                system = "x86_64-linux";
                modules = [ ./configuration.nix ];
            };
        };
    };

}
```

Note: make sure to change `hostname` to your own hostname.

Now we can rebuild our system using our newly created flake. Save `flake.nix` and exit. Run the following command to tell `nixos-rebuild` to use the flake in the current directory.

```bash
sudo nixos-rebuild switch --flake .
```

It will probably take a while to run the first time, this is because NixOS is pulling down the nixpkgs repo. It will run much faster in the future.

After the rebuild has completed, take a look inside your `.dotfiles` directory again. You should see a new file added called `flake.lock`. This file keeps track of the exact versions of the packages that get installed.

## nix-bitcoin

### flake.nix

Now that we have a basic NixOS configuration working, we can now add nix-bitcoin to our configuration using the flake approach.

Let's take a look at the [example flake](https://github.com/fort-nix/nix-bitcoin/blob/master/examples/flakes/flake.nix) in the nix-bitcoin repo.

So we first need to add nix-bitcoin to our flake inputs.

```nix
# flake.nix

{
  # ...

  inputs = {
    nixpkgs.url = "nixpkgs/nixos-unstable";
    nix-bitcoin.url = "github:fort-nix/nix-bitcoin/release";
  };

  # ...
}
```

Then we can include it in our outputs.

```nix
# flake.nix

{
    # ...

    outputs = {
      self,
      nixpkgs,
      nix-bitcoin,
      ... }:
    let
        lib = nixpkgs.lib;
    in {
        nixosConfigurations = {
            hostname = lib.nixosSystem {
                system = "x86_64-linux";
                modules = [
                    ./configuration.nix
                    nix-bitcoin.nixosModules.default
                    # Optionally enable the secure-node preset
                    # to enhance security and privacy.
                    (nix-bitcoin + "/modules/presets/secure-node.nix")
                    {
                      # Automatically generate all secrets required by services.
                      # The secrets are stored in /etc/nix-bitcoin-secrets
                      nix-bitcoin.generateSecrets = true;

                      # When using nix-bitcoin as part of a larger NixOS
                      # configuration, setting the follow enables interactive
                      # access to nix-bitcoin features (like bitcoin-cli) for
                      # your system's main user
                      nix-bitcoin.operator = {
                        enable = true;
                        name = "FIXME";
                      };
                    }
                ];
            };
        };
    };

}
```

Note: change `nix-bitcoin.operator.name` to your actual username. 

Rebuild again with `sudo nixos-rebuild switch --flake .`

Note: since we've enabled the secure node preset, we have disabled `sudo`. Use `doas` instead of `sudo` from now on. `doas` is a more secure alternative to `sudo`. [See more]()

### Adding services

Now that our NixOS system knows where to grab its nix-bitcoin packages, let's start adding some services.

Hint: you can see a list of example services in the [examples](https://github.com/fort-nix/nix-bitcoin/blob/master/examples/configuration.nix) provided by nix-bitcoin. 

There are several different ways to do this. For example, you can add them directly in the flake, or you can add them to your `configuration.nix` file. We are going to take a _modularised_ approach instead. This means that we will make a separate configuration file for each services and import them individually into our `configuration.nix` file. There are several advantages to using a modularised approach. By separating our configuration by individual services, we prevent the main configuration from becoming overcrowded and hard to read. It also makes it easier to troubleshoot the individual configurations without touching other services, as we can simply disable a service if it starts having problems without affecting other services.

To start, let's create as new directory inside our `.dotfiles` directory called `system/bitcoin` where we will keep our bitcoin-related nix files. You can call this whatever you like, just make sure you import the correct file path later on. 

```bash
mkdir system
mkdir system/bitcoin
cd system/bitcoin
```

Now let's write our `bitcoind.nix` file to configure bitcoind.

```bash
vim bitcoind.nix
```

```nix
# bitcoind.nix

{config, ...}: {
  services.bitcoind = {
    enable = true;
    prune = 0;
    txindex = true;
    zmqpubrawtx = "tcp://127.0.0.1:28333";
    zmqpubrawblock = "tcp://127.0.0.1:28332";
    listen = true;
    address = "0.0.0.0";
    # Listen to RPC connections on all interfaces
    rpc.address = "0.0.0.0";
    # Allow RPC connections from external addresses
    rpc.allowip = [
      "10.10.0.0/24" # Allow a subnet
      "10.50.0.3" # Allow a specific address
      "0.0.0.0/0" # Allow all addresses
    ];
  };
  networking.firewall.allowedTCPPorts = [
    config.services.bitcoind.port
    config.services.bitcoind.rpc.port
  ];
  # Set this to announce the onion service address to peers.
  # The onion service allows accepting incoming connections via Tor.
  nix-bitcoin.onionServices.bitcoind.public = true;
}
```

Note: change `rpc.allowip` to your specific network

And now import it into our `configuration.nix`

```nix
# configuration.nix

{ pkgs, ... }: {
    imports = [
        ./hardware-configuration.nix
        ./system/bitcoin/bitcoind.nix
    ];

    # ...
}
```

Rebuild the system. Remember we now use `doas` instead of `sudo`.

```bash
doas nixos-rebuild switch --flake .
```

After the rebuild, we should have a bitcoind service running. Let's check it by running

```bash
doas systemctl status bitcoind.service
```

Let's also check if our user has interactive access to commands like `bitcoin-cli`.

```bash
bitcoind --version
bitcoin-cli getblockchaininfo
```

To follow the live logs, use the following command

```bash
doas journalctl -fu bitcoind.service
```

To stop the service, run

```bash
doas systemctl stop bitcoind.service
```

To start it again, run

```bash
doas systemctl start bitcoind.service
```

The data directory of bitcoind is installed to `/var/lib/bitcoind` by nix-bitcoin. Let's take a look inside this directory. Since it is outside the home directory of our regular user, we first need to become root.

```bash
doas su
cd /var/lib/bitcoind
ls -al
```

Notice that these files are owned by the `bitcoin` user.

Try taking a look at our `bitcoin.conf` file.

```bash
cat bitcoin.conf
```

It reflects the configuration we've set up in `bitcoind.nix`. Nice.

Lastly, let's take a look at where nix-bitcoin is storing our secrets, like our rpc password. Still as the super user, navigate to `/etc/nix-bitcoin-secrets`

```bash
cd /etc/nix-bitcoin-secrets
ls -al
```

We can see that nix-bitcoin has automatically generated a bunch of password files for us, just like we told it to in our `flake.nix`.

### Bonus: migrate from existing node

You might already have a bitcoind instance with a fully synced blockchain and don't want to sync the chain all over again. The good news is that you simply copy the blockchain from the existing node.

1. Stop `bitcoind` on both nodes

```bash
doas systemctl stop bitcoind.service
```

2. Copy the data directory to the nix-bitcoin node

```bash
# Important: Add a trailing slash to the source path
rsync root@existing-bitcoin-node:/path/to/existing/bitcoind-datadir/ /var/lib/bitcoind
```

3. Fix permissions on the nix-bitcoin node

```bash
doas chown -R bitcoin: /var/lib/bitcoind
```

4. Start `bitcoind`

```bash
doas systemctl start bitcoind.service
```

You can use the same workflow for other services. See [source](https://github.com/fort-nix/nix-bitcoin/blob/master/docs/configuration.md#migrate-existing-services-to-nix-bitcoin) for more services.
