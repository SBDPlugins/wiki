---
description: An example panels.yml for ThemeParkConnector.
---

# Example panels.yml

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

