# Usage

### Commands:

* **/af info** - Information about the plugin
* **/af help** - Get list of commands
* **/af reload** - reload the plugin
* **/af create \<name>** - Create an itemframe section.
* **/af addframes \<name>** - Add one/more frame(s) to an itemframe section
* **/af take \<name> \<player>** - Take a picture of an/multiple user(s) and add it to the next available itemframe in an itemframe section.
  * The player can be either a name or a radius (r=5). _**You can't use the Minecraft selectors!**_
* **/af give \[user] \<imageuser>** - Give a User a picture of the ImageUser.
* **/af reset \<name> \<framenumber/all>** - Reset one/all itemframes
* **/af remove \<name>** - Remove an itemframe section.

### **Signs:**

_ActionFoto contains a_ [_Traincarts_ ](https://www.spigotmc.org/resources/traincarts.39592/)_sign._

\[train]\
actionfoto\
\<name>

### **Layer system:**

The existing layers are: **BACKGROUND** (full size image), **PLAYERSKIN** (replaces %UUID% by the player UUID), **IMAGE** (a normal image), **TEXT** (just text, use %PLAYERNAME% for the name of the player). See the examples below:

```yaml
#Background layer:
'1':
  Type: BACKGROUND
  Value: https://sbdplugins.nl/images/random.png
#Playerskin layer:
'1':
  Type: PLAYERSKIN
  Value: https://sbdplugins.nl/images/player3d.png?uuid=%UUID%
  X: 40 #X position, from top left
  Y: 40 #Y position, from top left
#Image player
'1':
  Type: IMAGE
  Value: https://sbdplugins.nl/images/random.png
  X: 30 #X position, from top left
  Y: 20 #Y position, from top left
  Width: 60 #Width (pixels)
  Height: 40 #Height (pixels)
#Text layer
'1':
  Type: TEXT
  Value: 'Hello!'
  X: 20 #X position, from top left
  Y: 30 #Y position, from top left
  #Font is optional!
  Font:
    Name: Tahoma #The font name (must be supported by java)
    Type: 0 #The font type (see below)
    Size: 8.0 #Font size (pixels)
```

You can find a list of available fonts [here](https://alvinalexander.com/blog/post/jfc-swing/swing-faq-list-fonts-current-platform/). The types are: **0** (Plain), **1** (Bold) and **2** (Italic).
