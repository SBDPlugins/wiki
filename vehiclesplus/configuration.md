---
description: This page describes all the options in your configuration files.
---

# Configuration

## config.yml

This is the default configuration file.

```yaml
config-version: 1.0.3
locale: en
canDriveOverSlabs: true
canDriveOverBlocks: true
repairCostDivision: 100.0
vehicleDamage: true
entityCollisionStop: true
entityCollisionDamageSelf: true
entityCollisionDamageEntity: true
renameCost: 1000.0
ownerChangeCost: 1000.0
onlySpawnOnSpawnpoints: false
showActionBar: true
```

### config-version

This value is used internally to determine whether or not to automatically update the `config.yml` file.

```yaml
config-version: 1.0.3
```

{% hint style="warning" %}
**Do not manually edit this value!** It may result in corruption of your files.
{% endhint %}

### locale

Changing this value allows you to change the language used for VehiclesPlus. The value must match a valid file under the `locale` folder.

```yaml
locale: en
```

### canDriveOverSlabs

Changes the ability to drive over half blocks, or slabs. Disabling this will prevent vehicles from automatically "climbing" over half slabs.

```yaml
canDriveOverSlabs: true
```

### canDriveOverBlocks

Changes the ability to drive over full blocks. Disabling this will prevent vehicles from automatically "climbing" over full blocks.

```yaml
canDriveOverBlocks: true
```

### repairCostDivision

The number to divide the vehicle's purchase cost by when repairing a vehicle. For example, when repairing a car that costs $15,000, by default, it will cost $150 to repair. `15000 / 100 = 150`

```yaml
repairCostDivision: 100.0
```

### vehicleDamage

Globally enable or disable vehicle damage. When disabled, vehicles will be invincible and take no damage on collision with other objects or entities.

```yaml
vehicleDamage: true
```

### entityCollisionStop

Will the vehicle come to a halt when it collides with an entity? Set to false to allow the vehicle to lose no speed when colliding with entities.

```yaml
entityCollisionStop: true
```

### entityCollisionDamageSelf

When colliding with an entity, should the vehicle take damage? Set to false to disable vehicle damage when colliding with entities.

```yaml
entityCollisionDamageSelf: true
```

### entityCollisionDamageEntity

When colliding with an entity, should the entity take damage? Set to false to disable entity damage when the entity is hit by a vehicle.

```yaml
entityCollisionDamageEntity: true
```

### renameCost

The price that it costs to rename your vehicle.

```yaml
renameCost: 1000.0
```

### ownerChangeCost

The price that it costs to transfer your vehicle to a new owner.

```yaml
ownerChangeCost: 1000.0
```

### onlySpawnOnSpawnpoints

Should vehicles only be able to spawn on a Spawnpoint? Set to false to allow vehicles to be spawned in anywhere.

```yaml
onlySpawnOnSpawnpoints: false
```

### showActionBar

Should an action bar with vehicle stats be shown while in the driver's seat? Set to false to disable.

```yaml
showActionBar: true
```

## sounds.yml

This is the default `sounds.yml` configuration file.

```yaml
sounds:
  examplecar-engine-idle:
    sound: car.idle
    duration: 6
  examplecar-engine-start:
    sound: car.start
    duration: 2
  examplecar-engine-accelerate:
    sound: car.accelerate
    duration: 2
  examplecar-engine-driving:
    sound: car.driving
    duration: 2
  examplecar-engine-slowingdown:
    sound: car.slowingdown
    duration: 2
```

### Understanding sounds.yml

Each vehicle can have its own sound effects associated with it. Currently, the example resource pack only provides sounds for the example car.&#x20;

There are **six** different types of sounds that can be made during a vehicle's motion:

* idle
* start
* accelerate
* driving
* slowingdown

Each sound corresponds to a specific type of motion that the vehicle can make.

#### idle

Sound produced when a vehicle is not in motion.

#### start

Sound produced when a vehicle starts up.

#### accelerate

Sound produced when a vehicle is speeding up.

#### driving

Sound produced when a vehicle is driving at a near-constant speed.

#### slowingdown

Sound produced when a car is slowing down.



The `sound` value corresponds to a specific sound file found in the resource pack. Additionally, the `duration` value corresponds to the sound's duration.

### Adding Custom Vehicle Sounds

Editing or adding vehicle sounds is quite simple.

1. Begin by duplicating the `examplecar` sound configuration in the `sounds.yml` file.
2. Edit the `examplecar` values to match the name of your vehicle. For example, if I had a vehicle named TestVehicle, I would change `examplecar-engine-idle` to `testvehicle-engine-idle`.
3. Add your sound files to your resource pack, under the `assets/minecraft/sounds` folder. It is highly recommended that you create an additional folder for your specific vehicle's sounds, such as `assets/minecraft/sounds/testvehicle`.

{% hint style="info" %}
The `sounds.yml` file is case insensitive. You may choose to change your car's name to be completely lowercase if you wish, as shown in the example above.
{% endhint %}

{% hint style="warning" %}
It is important to make sure that your sound files are in the `.ogg` format. Minecraft does not support any other sound format. An online MP3 to OGG converter can be found [here](https://audio.online-convert.com/convert-to-ogg).
{% endhint %}

## Adding your own language.

### Understanding Locale Files

Within a locale file, you are able to change the messages that are sent by VehiclesPlus. Every message sent by VehiclesPlus is completely customizable.

### Creating a Locale File

1. Begin by making a copy of the `lang_en.yml` file, located under `plugins/VehiclesPlus/locale`. This is the default English locale file.&#x20;
2. Rename the file to match the language that you are translating. For example, Spanish would be `lang_es.yml`. To view a list of standard 2 letter language names, click [here](https://www.sitepoint.com/iso-2-letter-language-codes/). You do not necessarily have to match these names, but it is recommended.
3. Once renamed, open the file and begin editing the messages. Once you are satisfied, save the file.
4. Open your `config.yml` file. Find the line that says `locale: en` and edit it to match the name of your locale file. For example, if I had created `lang_es.yml`, I would change the line to `locale: es`.
5. Save your `config.yml` and restart the server.

{% hint style="info" %}
Do not include the `lang`\_ prefix or `.yml` ending on the `locale: en` line in your configuration.
{% endhint %}
