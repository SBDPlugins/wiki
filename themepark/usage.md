# Usage

## ThemePark:

### Commands:

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

## ThemeParkConnector:

### Commands:

* **/tpc reload** - Reload the plugin.
* **/tpc redeem &lt;Voucher&gt;** - Redeem a voucher for a show.
* **/tpc state &lt;Attraction ID&gt; &lt;Button ID&gt; &lt;State ID&gt;** - Change the state of a button for an attraction at the online panel. Most of the time, you use this command in a commandblock.

### Signs:

#### _The ParkControl sign \[For the online panel\]:_

\[ParkControl\]  
&lt;Attraction ID&gt;

**Please make sure to setup a panel for your ride! You can find an example below:**

{% code title="panels.yml" %}
```yaml
panels:
  ride:
    permission: "park.ride"
    buttons:
      power:
        title: "Power"
        state: "off"
        states:
          on:
            text: "ON"
            command: "rsc off ridepower"
            image: "GREEN BUTTON URL"
          off:
            text: "OFF"
            command: "rsc on ridepower"
            image: "RED BUTTON URL"
      entrance:
        title: "Entrance"
        state: "closed"
        states:
          open:
            text: "Open"
            command: "rsc off rideentrance"
            image: "GREEN BUTTON URL"
          closed:
            text: "Closed"
            command: "rsc on rideentrance"
            image: "RED BUTTON URL"
      depart:
        title: "Depart"
        state: "rejected"
        states:
          allowed:
            text: "Allowed"
            command: "rsc ridedepart"
            image: "GREEN BUTTON URL"
          rejected:
            text: "Rejected"
            command: ""
            image: "RED BUTTON URL"
      restraints:
        title: "Restraints"
        state: "closed"
        states:
          open:
            text: "Open"
            command: "rsc off rideres"
            image: "GREEN BUTTON URL"
          closed:
            text: "Closed"
            command: "rsc on rideres"
            image: "RED BUTTON URL"
      gates:
        title: "Gates"
        state: "closed"
        states:
          open:
            text: "Open"
            command: "rsc off ridebrackets"
            image: "GREEN BUTTON URL"
          closed:
            text: "Closed"
            command: "rsc on ridebrackets"
            image: "RED BUTTON URL"
      malfunction:
        title: "Report malfunction"
        state: "notreported"
        states:
          reported:
            text: "Reported"
            command: ""
            image: "RED BUTTON URL"
          notreported:
            text: "Not Reported"
            command: "rsc ridemalfunction"
            image: "EMERGENCY BUTTON URL"
```
{% endcode %}

#### _The Ticket sign \[For the online panel\]:_

\[Scanner Tag\]  
&lt;Show ID&gt;

**Please note that the scanner tag can be found in settings.yml.**

## ThemeParkPlus:

### Commands:

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

### Signs:

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

_**Malfunction GUI:**_

\[ThemeParkPlus\]  
_****_Malfunction  
&lt;RideID&gt;



