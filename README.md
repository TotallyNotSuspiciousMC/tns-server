# TNS Server Mod Pack

A modpack to manage the basic server files for the Totally Not Suspicious SMP. This is a **server-side and vanilla-compatible** modpack for Fabric 26.2.

## Building / Exporting

This pack is managed using [packwiz](https://packwiz.infra.link/).[^1] It can be exported to a `.mrpack` for distribution using the following command:

```
packwiz modrinth export
```

[^1]: The build artifacts for packwiz often expire. I have a fork of Packwiz where you can maybe get the artifact from here, if the official one is not updated: https://github.com/TotallyNotSuspiciousMC/packwiz/actions

## Installing with unsup

The preferred method for installing and using this modpack on a server is with [unsup](https://git.sleeping.town/exa/unsup). The server uses the following `unsup.ini` configuration:

```ini
version=1
source_format=packwiz
source=https://raw.githubusercontent.com/TotallyNotSuspiciousMC/tns-server/refs/heads/main/pack.toml
no_gui=true
preset=minecraft
```

## Setup

This mod pack deliberately does not contain all config files used by TNS. Specifically, it does not include any 'live' or sensitive information like permission settings, the whitelist, the Discord bot token, and database credentials. If you want to create your own instance of TNS you will need to configure those on your local server after installing the mod pack.

To configure your local instance of TNS you will need to make the following configuration changes:

1. Start the server once and stop it to generate configuration files.
2. Add a Discord bot token to `./config/Discord-Integration.toml` (it should be near the top).
3. Add external database credentials to `./config/ledger.toml` in the format specified by [Ledger Databases](https://github.com/QuiltServerTools/Ledger-Databases).
4. Setup squaremap:
   1. Open the port `25566` on your server, or edit the port used in `./squaremap/config.yml`. You should probably not use `25565` since that is the port the Minecraft server will also use.
   2. Edit the web address to be given to players using the squaremap command in `./squaremap/config.yml`. Unless you use port `443`, this address will need to include the port at the end of the URL.
5. Alternatively, remove the following mod jar files. 
   - `dcintegration-*.jar`: This will mean that Discord chat integration will not work.
   - `ledger-databases-*.jar`: This mod is only used for an external database. Ledger will still work, but it will use a local SQLite database that is in my experience slower and less reliable than MariaDB. But whichever you use depends on how you host the server.