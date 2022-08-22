---
description: A tutorial on how to create new rims.
---

# Adding new rims

1. Go into the rims folder and copy the Default.yml
2. Rename the newly copied file to the new rim you want to make
3. Open the newly created file, it should look something like this:

```yaml
className: me.legofreak107.vehiclesplus.vehicles.objects.rims.RimDesign
skin:
  ==: org.bukkit.inventory.ItemStack
  type: LEATHER_CHESTPLATE
  damage: 2
  meta:
    ==: ItemMeta
    meta-type: LEATHER_ARMOR
    Unbreakable: true
price: 1000.0
name: default
```

&#x20;   4\. Edit the values in this file to match your desired rim design.\
&#x20;   5\. Reload the plugin using `/v reload`
