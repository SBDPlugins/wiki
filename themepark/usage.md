# Usage

## ThemePark:

### Commands:

* **/themepark help** - Displays the help menu.&#x20;
* **/themepark list** - Displays a list of all attractions.&#x20;
* **/themepark warp \<Attraction ID>** - Teleport to an attraction.&#x20;
* **/themepark toggle item** - Toggles the join item on or off.&#x20;
* **/themepark getitem \[Player]** - Give the item to yourself or another player.&#x20;
* **/themepark region create \<Region ID> \<Name>** - Create a region with id and name
* **/themepark region name \<Region ID> \<New Name>** - Change the name of a region.&#x20;
* **/themepark region remove \<Region ID>** - Remove region with ID including it's attractions
* **/themepark attraction create \<Region ID> \<Attraction ID> \<type> \<name>** - Create an attraction in region. Type can be **RIDE,** **SHOW** or **GLOBAL**
* **/themepark attraction name \<Attraction ID> \<New Name>** - Change the name of a attraction.&#x20;
* **/themepark attraction status \<Attraction ID> \<New Status>** - Change the status of an attraction.&#x20;
* **/themepark attraction location \<Attraction ID>** - Set the location of an attraction to your current location.&#x20;
* **/themepark attraction remove \<Attraction ID>** - Remove attraction with ID
* **/status** - Opens the menu.
* **/ridecount help** - Display the help menu.
* **/ridecount get \<Player Name> \<Attraction ID>** - Get players ridecount for attraction
* **/ridecount add \<Selector> \<Attraction ID> \<amount>** - Add certain amount to ridecount for one player by username or using selectors like **@p**

You can change the /themepark command to a custom command in the config! \
**<> is required and \[] is optional**

**The statusses you can use:** OPEN, CLOSED, MAINTENANCE, CONSTRUCTION, MALFUNCTION. Also you can use ACTIVE and INACTIVE if it is a show.

## ThemeParkConnector:

### Commands:

* **/tpc reload** - Reload the plugin.
* **/tpc redeem \<Voucher>** - Redeem a voucher for a show.
* **/tpc state \<Attraction ID> \<Button ID> \<State ID>** - Change the state of a button for an attraction at the online panel. Most of the time, you use this command in a commandblock.

### Signs:

#### _The ParkControl sign \[For the online panel]:_

\[ParkControl]\
\<Attraction ID>

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

#### _The Ticket sign \[For the online panel]:_

\[Scanner Tag]\
\<Show ID>

**Please note that the scanner tag can be found in settings.yml.**

## ThemeParkPlus:

### Commands:

* **/themeparkplus opengate \<World> \<X> \<Y> \<Z> \[ARG 1] \[ARG 2]** - This command opens a gate.\
  If you fill in a number of players in ARG 1, it will close if that amount of players passed the gate. If you fill in a direction in ARG 1, it will only let the players through the gate if the walk in that direction.\
  If you fill in a direction in ARG 2, it will only let the players through the gate if the walk in that direction. But you also need to use ARG 1, with a amount of players for this.
* **/themeparkplus closegate \<World> \<X> \<Y> \<Z>** - This command closes a gate.
* **/themeparkplus lampon \<World> \<X> \<Y> \<Z> \[Seconds on]** - This command will turn on a redstone lamp. If you fill in an amount of seconds, it will go off after that amount of seconds.
*   **/themeparkplus lampoff \<World> \<X> \<Y> \<Z>**

    &#x20;\- This command will turn off a redstone lamp.
* **/themeparkplus lampson \<World> \<X1> \<Y1> \<Z1> \<X2> \<Y2> \<Z2> \[Seconds on]** - This command will turn on all the redstone lamps in the region. If you fill in an amount of seconds, they will go off after that amount of seconds.
*   **/themeparkplus lampsoff \<World> \<X> \<Y> \<Z>**

    &#x20;\- This command will turn off all the redstone lamps in the region.

You can change the /themepark command to a custom command in the ThemePark config! It will automaticly paste plus behind it. So if you choose /hello, it will make /helloplus of it.\
**<> is required and \[] is optional**

### Signs:

_**Fastpass Machine:**_&#x20;

\[ThemeParkPlus] \
Machine\
\<Ride ID>\
\<Cost>

_**Fastpass Checker:**_&#x20;

\[ThemeParkPlus]\
Scanner\
\<RideID>\
\<Teleport or gate location -> X:Y:Z>

_**Waitingrow:**_&#x20;

_Please note, if you create your first waitingrow for an attraction, that you have to make a selection of the row with the WorldEdit wand (left click for Pos1, right click for Pos2), and create an WorldGuard region with that selection._

\[ThemeParkPlus] \
WaitingRow\
\<Ride ID>\
\[Region ID]

_The Region ID is only needed if it's the first sign for that Ride._

_**Malfunction GUI:**_

\[ThemeParkPlus]\
_****_Malfunction\
\<RideID>

