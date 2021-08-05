# Examples

## VehiclesPlus:

### Example 1: Broadcast warning if player is driving too fast

This code will broadcast a waning to everyone with the permission **myplugin.staff** if someone drives more than 80 km/h. There is a cooldown of 5 seconds, so that there is no spam.

```java
private final WeakHashMap<UUID, LocalDateTime> cooldown = new WeakHashMap<>();

@EventHandler
public void onSendKey(SendKeyEvent e) {
    /* STEP 1: Get the driver */
    Player driver = e.getDriver();

    /* STEP 2: Convert Entity to SpawnedVehicle */
    Entity seatArmorstand = e.getRiding();
    if (!seatArmorstand.hasMetadata("PART_DATA")) return; //It's not a part? Skip for now.
    Part part = (Part) seatArmorstand.getMetadata(NBTDataType.PART_DATA.name()).get(0).value(); //Convert to a Part
    if (part == null) return; //The part is null? Skip for now.
    SpawnedVehicle v = part.getOwningVehicle();

    /* STEP 3: Check speed */
    if (v.getCurrentSpeedInKm() > 80) {
        /* STEP 4: Check if driver has no cooldown, and send speedwarning */
        if (!hasCooldown(driver)) Bukkit.broadcast(ChatColor.GOLD + driver.getName() + ChatColor.WHITE + " drives too fast! Current speed: " + ChatColor.GOLD + v.getCurrentSpeedInKm(), "myplugin.staff");
    }
}

private boolean hasCooldown(Player driver) {
    boolean hasCooldown = false;
    if (cooldown.containsKey(driver.getUniqueId())) {
        LocalDateTime past = LocalDateTime.now();
        LocalDateTime now = cooldown.get(driver.getUniqueId());
        int seconds = (int) ChronoUnit.SECONDS.between(now, past);
        if (seconds > 5) {
            cooldown.remove(driver.getUniqueId());
        }
    } else {
        cooldown.put(driver.getUniqueId(), LocalDateTime.now());
        hasCooldown = true;
    }

    return hasCooldown;
}
```



