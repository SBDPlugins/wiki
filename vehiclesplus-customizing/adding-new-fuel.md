# Adding new fuel

1. Go into the fuels folder and copy the Gasoline.yml
2. Rename the newly copied file to the new fuel you want to make
3. Open the newly created file. It should look something like this:

```yaml
className: me.legofreak107.vehiclesplus.vehicles.objects.fuel.FuelType
name: Gasoline
pricePerLiter: 1.5
fuelItem:
  ==: org.bukkit.inventory.ItemStack
  type: LAVA_BUCKET
```

&#x20;  4\. Edit the values in this file to match your desired rim design.\
&#x20;  5\. Reload the plugin with `/v reload`
