# TNS Server Mod Pack

A modpack to manage the basic server files for the Totally Not Suspicious SMP. This is a **server-side and vanilla-compatible** modpack for Fabric 26.2.

> ![NOTE]
> This mod pack does not contain all config files used by TNS. Specifically, it does not include any 'live' or sensitive information like permission settings, and the whitelist, Discord bot and database credentials. If you want to create your own instance of TNS you will need to configure those on your local server after installing the mod pack.

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