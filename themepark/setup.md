# Setup

## ThemePark:

Just [download the plugin on Spigot](https://www.spigotmc.org/resources/themepark.48648/), and put the JAR file into your **/plugins** folder. The plugin will do everything for you, and you can change everything in the files. If you want to use all the functions of ThemeParkPlus Basic, you have to do some more things.

## ThemeParkPlus:

For ThemeParkPlus you need [WorldEdit ](https://dev.bukkit.org/projects/worldedit)and [WorldGuard ](https://dev.bukkit.org/projects/worldguard)for the waiting row system, and [Vault ](https://dev.bukkit.org/projects/vault/files)for the FastPass system. Just put all the plugins in you **/plugins** **folder** and **restart** the server.

## ThemeParkConnector:

_This plugin is only required if you want to use ThemeParkPanel\(Plus\). It will connect your Minecraft server with our panel._

Just put this plugin in your **/plugins folder**. ****For usage with the panel, you have to connect **ThemePark** to the database that you're going to use for the panel. Please see _**step 2**_ of the ThemeParkPanel installation.

If you're going to install the **ThemeParkPanelPlus**, you have to change some things in the settings.yml of the **ThemeParkConnector.** Change it to something like this:

{% code title="settings.yml" %}
```yaml
socket:
  enabled: true
  url: "wss://websocket.iobyte.nl/"
  panel: "https://panel.domain/panel/panel/"
  id: "CHANGEME"
```
{% endcode %}

_You don't have to touch the **url**._ At the **panel**, you have to change it to the **panel URL**. If your panel is located at **https://something.com/panel**, then you have to enter **https://something.com/panel/panel/** there. Also, you have to make up an ID, that is **unique** for your server, like your **server name**. Put it at the **id**.

