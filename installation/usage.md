# The Usage

Now you can use the plugins and panels. Here we will give you some help about using them.

## The commands:

### ThemePark:

* **/themepark help** - Displays the help menu. 
* **/themepark list** - Displays a list of all attractions. 
* **/themepark warp &lt;Attraction ID&gt;** - Teleport to an attraction. 
* **/themepark toggle item** - Toggles the join item on or off. 
* **/themepark getitem \[Player\]** - Give the item to yourself or another player. 
* **/themepark region create &lt;Region ID&gt; &lt;Name&gt;** - Create a region with id and name
* **/themepark region name &lt;Region ID&gt; &lt;New Name&gt;** - Change the name of a region. 
* **/themepark region remove &lt;Region ID&gt;** - Remove region with ID including it's attractions
* **/themepark attraction create &lt;Region ID&gt; &lt;Attraction ID&gt; &lt;type&gt; &lt;name&gt;** - Create an attraction in region. Type can be **RIDE,** **SHOW** or **GLOBAL**
* **/themepark attraction name &lt;Attraction ID&gt; &lt;New Name&gt;** - Change the name of a attraction. 
* **/themepark attraction status &lt;Attraction ID&gt; &lt;New Status&gt;** - Change the status of an attraction. 
* **/themepark attraction location &lt;Attraction ID&gt;** - Set the location of an attraction to your current location. 
* **/themepark attraction remove &lt;Attraction ID&gt;** - Remove attraction with ID
* **/status** - Opens the menu.
* **/ridecount help** - Display the help menu.
* **/ridecount get &lt;Player Name&gt; &lt;Attraction ID&gt;** - Get players ridecount for attraction
* **/ridecount add &lt;Selector&gt; &lt;Attraction ID&gt; &lt;amount&gt;** - Add certain amount to ridecount for one player by username or using selectors like **@p**

You can change the /themepark command to a custom command in the config!   
**&lt;&gt; is required and \[\] is optional**

**The statusses you can use:** OPEN, CLOSED, MAINTENANCE, CONSTRUCTION, MALFUNCTION. Also you can use ACTIVE and INACTIVE if it is a show.

### ThemeParkConnector:

* **/tpc reload** - Reload the plugin.
* **/tpc redeem &lt;Voucher&gt;** - Redeem a voucher for a show.
* **/tpc state &lt;Attraction ID&gt; &lt;Button ID&gt; &lt;State ID&gt;** - Change the state of a button for an attraction at the online panel. Most of the time, you use this command in a commandblock.

#### The signs:

#### _The ParkControl sign \[For the online panel\]:_

\[ParkControl\]  
&lt;Attraction ID&gt;

**Please also see the** [**Example panels.yml**](../other-things/example-panels.md) **page.**

#### _The Ticket sign \[For the online panel\]:_

\[Scanner Tag\]  
&lt;Show ID&gt;

**Please note that the scanner tag can be found in settings.yml.**

### ThemeParkPlus:

* **/themeparkplus opengate &lt;World&gt; &lt;X&gt; &lt;Y&gt; &lt;Z&gt; \[ARG 1\] \[ARG 2\]** - This command opens a gate. If you fill in a number of players in ARG 1, it will close if that amount of players passed the gate. If you fill in a direction in ARG 1, it will only let the players through the gate if the walk in that direction. If you fill in a direction in ARG 2, it will only let the players through the gate if the walk in that direction. But you also need to use ARG 1, with a amount of players for this.
* **/themeparkplus closegate &lt;World&gt; &lt;X&gt; &lt;Y&gt; &lt;Z&gt;** - This command closes a gate.
* **/themeparkplus lampon &lt;World&gt; &lt;X&gt; &lt;Y&gt; &lt;Z&gt; \[Seconds on\]** - This command will turn on a redstone lamp. If you fill in an amount of seconds, it will go off after that amount of seconds.
* **/themeparkplus lampoff &lt;World&gt; &lt;X&gt; &lt;Y&gt; &lt;Z&gt;**

   - This command will turn off a redstone lamp.

* **/themeparkplus lampson &lt;World&gt; &lt;X1&gt; &lt;Y1&gt; &lt;Z1&gt; &lt;X2&gt; &lt;Y2&gt; &lt;Z2&gt; \[Seconds on\]** - This command will turn on all the redstone lamps in the region. If you fill in an amount of seconds, they will go off after that amount of seconds.
* **/themeparkplus lampsoff &lt;World&gt; &lt;X&gt; &lt;Y&gt; &lt;Z&gt;**

   - This command will turn off all the redstone lamps in the region.

You can change the /themepark command to a custom command in the ThemePark config! It will automaticly paste plus behind it. So if you choose /hello, it will make /helloplus of it.  
**&lt;&gt; is required and \[\] is optional**

#### The signs:

_**Fastpass Machine:**_ 

\[ThemeParkPlus\]   
Machine  
&lt;Ride ID&gt;  
&lt;Cost&gt;

_**Fastpass Checker:**_ 

\[ThemeParkPlus\]  
Scanner  
&lt;RideID&gt;  
&lt;Teleport or gate location -&gt; X:Y:Z&gt;

_**Waitingrow:**_ 

_Please note, if you create your first waitingrow for an attraction, that you have to make a selection of the row with the WorldEdit wand \(left click for Pos1, right click for Pos2\), and create an WorldGuard region with that selection._

\[ThemeParkPlus\]   
WaitingRow  
&lt;Ride ID&gt;  
\[Region ID\]

_The Region ID is only needed if it's the first sign for that Ride._

### ActionFoto:

* **/af info** - Information about the plugin
* **/af help** - Get list of commands
* **/af reload** - reload the plugin
* **/af create &lt;name&gt;** - Create an itemframe section.
* **/af addframes &lt;name&gt;** - Add one/more frame\(s\) to an itemframe section
* **/af take &lt;name&gt; &lt;player&gt;** - Take a picture of an/multiple user\(s\) and add it to the next available itemframe in an itemframe section.
  * The player can be either a name or a radius \(r=5\). _**You can't use the Minecraft selectors!**_
* **/af give \[user\] &lt;imageuser&gt;** - Give a User a picture of the ImageUser.
* **/af reset &lt;name&gt; &lt;framenumber/all&gt;** - Reset one/all itemframes
* **/af remove &lt;name&gt;** - Remove an itemframe section.

**The signs:**

_ActionFoto contains a_ [_Traincarts_ ](https://www.spigotmc.org/resources/traincarts.39592/)_sign._

\[train\]  
actionfoto  
&lt;name&gt;

**Usage of layer system:**

The existing layers are: **BACKGROUND** \(full size image\), **PLAYERSKIN** \(replaces %UUID% by the player UUID\), **IMAGE** \(a normal image\), **TEXT** \(just text, use %PLAYERNAME% for the name of the player\). See the examples below:

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

You can find a list of available fonts [here](https://alvinalexander.com/blog/post/jfc-swing/swing-faq-list-fonts-current-platform/). The types are: **0** \(Plain\), **1** \(Bold\) and **2** \(Italic\).

### ThemePark Ridecount Add-on:

* **/tprc info** - Information about the plugin
* **/tprc help** - Get list of commands
* **/tprc create &lt;RideID&gt; &lt;UpdateFrequency&gt;** - Create a ridecount itemframe.
  * The UpdateFrequency is NEVER, DAILY or WEEKLY.
* **/tprc update &lt;RideID&gt;** - Force the update of a ridecount itemframe.
* **/tprc remove &lt;RideID&gt;** - Remove a ridecount itemframe.

## The permissions:

### ThemePark:

* themepark.item - For using toggleitem and getitem 
* themepark.admin - All the other functions who are for admins!

### ThemeParkPlus:

* ThemeParkPlus.OpenGate - The opengate command permission 
* ThemeParkPlus.CloseGate - The closegate command permission 
* ThemeParkPlus.LampOn - The lampoff command permission 
* ThemeParkPlus.LampOff - The lampoff command permission 
* ThemeParkPlus.CreateFPSign - The fastpass sign create permission

### ThemeParkConnector:

* themepark.admin - All the other functions who are for admins!
* themepark.control - Needed to control attractions on the panel

### ActionFoto:

* AF.admin - The general admin permission
* AF.give - The give command permission

### ThemePark Ridecount Add-on:

* TPRC.admin - The general admin permission \(for all the commands\)





