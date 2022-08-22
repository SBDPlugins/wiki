---
description: How to install and configure VehiclePlus.
---

# Setup

## Installing the plugin

Just [download the plugin on Spigot](https://www.spigotmc.org/resources/themepark.48648/) or Polymart, and put the JAR file into your **/plugins** folder. The plugin will do everything for you, and you can change everything in the files. If you want to use all the functions of VehiclePlus, you have to do some more things.

### Downloading the dependencies:

Begin by downloading the latest versions of both [Vault ](https://www.spigotmc.org/resources/vault.34315/)and [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/). VehiclesPlus **requires** these plugins for various features. Vault does need a economy plugin to work propperly, one just like for example [EssentialsX](https://www.spigotmc.org/resources/essentialsx.9089/)

## (Optional) Installing your Resource Pack

VehiclesPlus makes use of resource packs to display the 3D models of a vehicle.

1. Because Minecraft changes resource pack formats quite often, we have designed a few example resource packs for your convenience. You can download the version that matches your server version [here](https://github.com/relavis/VehiclesPlus/tree/master/Resource%20Packs).&#x20;
2. Once you have downloaded the version that corresponds to your server version, you must upload the resource pack as a `.zip` file to a file sharing site of your choice, such as [Google Drive](https://drive.google.com), [Dropbox](https://www.dropbox.com), or similar.
3. Now that it is uploaded, it is time to edit your `server.properties` file. This file is located in the root directory of your server. Look for the line called `resource-pack=` and add the URL of the resource pack’s download link to the end of the line. It should look like this:

```
resource-pack=https://yourdomain.com/ResourcePack.zip
```

Make sure to save and restart your server after applying these changes.

{% hint style="warning" %}
Your URL must be a **direct link** to your resource pack! If it does not end in `.zip`, Minecraft will be unable to recognize the link, and therefore unable to download the resource pack.
{% endhint %}

## (Optional) Editing your configuration

Once your server has been restarted, you will have new configuration files under `plugins/VehiclesPlus`. Take a look at our [Configuration page](configuration/) to determine whether you would like to change your configuration. Once you have edited the configurations, save your files and restart the server.

## Setting Up Permissions

Depending on how you'd like to use your server, you may have to set up permissions. We suggest using [LuckPerms](https://luckperms.net) to set up permissions.

A list of permissions for VehiclesPlus can be found [here](permissions.md).
