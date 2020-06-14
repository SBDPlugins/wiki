# The Usage

Now you can use the plugins and panels. Here we will give you some help about using them.

## The commands:

### ThemePark:

* **/themepark help** - Displays the help menu. 
* **/themepark list** - Displays a list of all attractions. 
* **/themepark warp &lt;Attraction ID&gt;** - Teleport to an attraction. 
* **/themepark toggle item** - Toggles the join item on or off. 
* **/themepark getitem \[Player\]** - Give the item to yourself or another player. 
* **/themepark reload** - Reload the plugin. 
* **/themepark regionname &lt;RegionID&gt; &lt;New Name&gt;** - Change the name of a region. 
* **/themepark regionlore &lt;RegionID&gt; &lt;Index&gt; &lt;New Lore&gt;** - Change the lore of a region. For index use 0 for the first line, and 1 for the second line... You can use \_ for a space.
* **/themepark setlocation &lt;Attraction ID&gt;** - Set the location of an attraction to your current location. 
* **/themepark attraction &lt;Attraction ID&gt; &lt;New Status&gt;** - Change the status of an attraction. 
* **/status** - Opens the menu.

You can change the /themepark command to a custom command in the config!   
**&lt;&gt; is required and \[\] is optional**

**The statusses you can use:** OPEN, CLOSED, MAINTENANCE, CONSTRUCTION, MALFUNCTION. Also you can use ACTIVE and INACTIVE if it is a show.

### ThemeParkConnector:

* **/tpc reload** - Reload the plugin.
* **/tpc ridecount &lt;Attraction ID&gt; &lt;Selector&gt;** - Add one ride count to a/multiple player\(s\).
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

_**Not available yet in the v2.0 beta!**_

_Please note, if you create your first waitingrow for an attraction, that you have to make a selection of the row with a stick \(left click for Pos1, right click for Pos2\)._ 

\[ThemePark\]   
WaitingRow  
&lt;Ride ID&gt;

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





