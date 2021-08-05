# Commands

## Vehicles Commands \(/vehicles\)

Aliases: `/vp`, `/vehicle`, `/v`

### /v list

Display a list of the loaded vehicles across the server.

```text
/v list
```

 **Permission:** vp.admin.list

### /v give

Give a vehicle to a player.

```text
/v give (player) (vehicle) [red] [green] [blue]
```

 **Permission:** vp.admin.give

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| player | The username of the player that you want to give a vehicle to | relavis |  |
| vehicle | The name of the vehicle | ExampleCar |  |
| red | \(Optional\) A value between 0 and 255 for the red value of the vehicle | 150 | 255 |
| green | \(Optional\) A value between 0 and 255 for the green value of the vehicle | 150 | 255 |
| blue | \(Optional\) A value between 0 and 255 for the blue value of the vehicle | 150 | 255 |

### /v garage 

Open your vehicle garage.

```text
/v garage
```

**Permission:** vp.garage

### /v forceshop

Force open the vehicle shop for a player.

```text
/v forceshop (player)
```

**Permission:** vp.admin.forceshop.vehicles

### /v forcegarage

Force open the garage for a player.

```text
/v forcegarage (player)
```

**Permission:** vp.admin.forcegarage

### /v shop

Open the vehicle shop.

```text
/v shop
```

**Permission:** vp.shop

### /v info

Display more in-depth info about a vehicle.

```text
/v info (vehicle)
```

**Permission:** vp.admin.info

####  

## Fuel Commands \(/fuel\)

Aliases: `/vpfuel`, `/vpf`, `/fuels`

### **/fuel give**

Give a bucket of fuel to a player.

```text
/fuel give (player)
```

**Permission:** vp.admin.fuel.give

### /fuel buy

Buy a filled bucket of fuel.

```text
/fuel buy
```

**Permission:** vp.fuel.buy

### /fuel forceshop

Force open the fuel shop for a player.

```text
/fuel forceshop (player)
```

**Permission:** vp.admin.forceshop.fuel

### /fuel shop

Open the fuel shop.

```text
/fuel shop
```

**Permission:** vp.fuel.shop

####  

## Addon Commands \(/addon\)

Aliases: `/vpaddon`, `/vaddon`, `/addons`

### /addon givepart

Give a vehicle part to a player.

```text
/addon givepart (player) [red] [green] [blue] [foward offset] [up offset] [right offset]
```

**Permission:** vp.admin.givepart

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| player | The username of the player that you want to give a part to | relavis |  |
| red | \(Optional\) A value between 0 and 255 for the red value of the part | 150 | 255 |
| green | \(Optional\) A value between 0 and 255 for the green value of the part | 150 | 255 |
| blue | \(Optional\) A value between 0 and 255 for the blue value of the part | 150 | 255 |
| forward offset | \(Optional\) The amount forward to offset the part | 10 | 0 |
| up offset | \(Optional\) The amount up to offset the part | 10 | 0 |
| right offset | \(Optional\) The amount left/right to offset the part | 10 | 0 |

### /addon givepaint

Give paint to a player

```text
/addon givepaint (player) [red] [green] [blue]
```

**Permission:** vp.admin.givepaint

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| player | The username of the player that you want to give paint to | relavis |  |
| red | \(Optional\) A value between 0 and 255 for the red value of the paint | 150 | 255 |
| green | \(Optional\) A value between 0 and 255 for the green value of the paint | 150 | 255 |
| blue | \(Optional\) A value between 0 and 255 for the blue value of the paint | 150 | 255 |

### /addon givewheel

Give a wheel to a player

```text
/addon givewheel (player) (wheel) [red] [green] [blue]
```

**Permission:** vp.admin.givewheel

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| player | The username of the player that you want to give a wheel to | relavis |  |
| wheel | The type of wheel that you want to give | Wheel |  |
| red | \(Optional\) A value between 0 and 255 for the red value of the wheel | 150 | 255 |
| green | \(Optional\) A value between 0 and 255 for the green value of the wheel | 150 | 255 |
| blue | \(Optional\) A value between 0 and 255 for the blue value of the wheel | 150 | 255 |

