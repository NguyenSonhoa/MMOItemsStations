# MMOItems Stations

**MMOItems Stations** is a powerful and flexible Spigot/Paper plugin designed to create an in-depth item upgrade system for MMOItems. With an intuitive graphical interface and high customizability, you can create a unique upgrade experience for your players.

I hate to write these mf description.

---

## ✨ Features
- **Upgrade, Evolution.**
  **Anchor yml section**: you can copy paste make it clean in items.yml
- **GUI-Based Upgrading**: A user-friendly graphical interface that allows players to easily place items, preview, and perform upgrades.
- **Limitless Customization**:
    - **Costs & Materials**: Customize upgrade costs (requires [Vault](https://www.spigotmc.org/resources/vault.34315/)) and the required materials (supports both Vanilla and MMOItems).
    - **Per-Item Configuration**: Create unique upgrade paths for each item in the `items.yml` file.
    - **Stat Customization**: Define which stats are improved and by how much per level.
- **Item Preview**: Players can see the exact stats of the item after a successful upgrade.
- **Dynamic Stat Formatting**: Full control over how stats are displayed in the preview, for example, showing `CRITICAL_STRIKE_CHANCE` as a percentage (`%`).
- **CustomModelData Support**: Easily integrate with your server's resource pack by assigning CustomModelData to GUI items and buttons.
- **Admin Commands**: `/upgrade reload` to reload configurations and `/upgrade open <player>` to remotely open the GUI for other players.
- **User Experience**: Supports shift-clicking for quick item placement.
- **Custom Messages & Sounds**: Customize all messages and sounds for success or failure actions.

---

## ⚙️ Installation

1.  Buy plugin from Polymart or Blockmart.app
2.  Place the `.jar` file into your server's `plugins` folder.
3.  Install the required dependencies:
    *   [MMOItems](https://www.spigotmc.org/resources/mmoitems.39267/)
    *   [MythicLib](https://www.spigotmc.org/resources/mmolib-mythiclib.90306/)
    *   [Vault](https://www.spigotmc.org/resources/vault.34315/) (and an economy plugin like [EssentialsX](https://essentialsx.net/))
4.  Restart the server. The `config.yml` and `items.yml` configuration files will be generated automatically.

---

## ⌨️ Commands & Permissions

| Command | Description | Permission | User |
| :--- | :--- | :--- | :--- |
| `/upgrade` | Opens the item upgrade interface. | `mmoitemsstations.use` | Player |
| `/upgrade reload` | Reloads the configuration files. | `mmoitemsstations.admin.reload` | Admin |
| `/upgrade open <player>` | Opens the upgrade GUI for a specific player. | `mmoitemsstations.admin.open` | Admin, Console |
| `/upgrade setlevel <level> <player>` | Set level of weapon for player. | `mmoitemsstations.setlevel` | OP, Console |
---

## 🔧 Configuration

The plugin offers deep customization through two main files: `config.yml` and `items.yml`.

### `config.yml`

This file contains global settings for the GUI, default values, messages, sounds, and formats.

**Example of GUI customization with CustomModelData:**
```yaml
upgrade-gui:
  title: "&8Upgrade Station"
  size: 27
  slots:
    upgrade-item: 10
    preview-item: 12
    confirm-button: 16
  filler:
    material: "GRAY_STAINED_GLASS_PANE"
    name: " "
    custom-model-data: 10001
  items:
    confirm-button:
      material: "LIME_STAINED_GLASS_PANE"
      name: "&a&lCONFIRM"
      custom-model-data: 10002
      lore:
        - "&7Click to upgrade the item."
        - "&7Cost: &e%cost%$"
        - "&7Materials:"
        - "%materials%"
    no-item-button:
      material: "RED_STAINED_GLASS_PANE"
      name: "&c&lNO ITEM"
      custom-model-data: 10003
      lore:
        - "&7Place an item in the left slot."
```

**Example of stat formatting:**
```yaml
stat-formats:
  # Default format for unlisted stats
  default: "&7%stat%: &f%original% &7-> &a%new% &e(+%diff%)"
  # Specific format for certain stats (add '%%' to display the percent sign)
  specific:
    CRITICAL_STRIKE_CHANCE: "&9%stat%: &f%original%% &7-> &a%new%% &e(+%diff%%)"
    CRITICAL_STRIKE_POWER: "&9%stat%: &f%original%% &7-> &a%new%% &e(+%diff%%)"
```

### `items.yml`

This file allows you to define unique upgrade paths for individual MMOItems.

**Syntax:**
```yaml
items:
  # MMOItems Type (e.g., SWORD, AXE, ARMOR)
  SWORD:
    # ID of the MMOItem
    EXCALIBUR:
      max-level: 15
      cost:
        vault:
          base-cost: 5000.0
          increase-per-level: 1000.0
      # Stats to be increased by a percentage per level
      stat-increase-percent:
        ATTACK_DAMAGE: 8.0
        ATTACK_SPEED: 0.5
        CRITICAL_STRIKE_CHANCE: 1.0
      # List of required materials
      materials:
        - type: "VANILLA"
          id: "DIAMOND_BLOCK"
          display-material: "Diamond Block" # Display name for the Vanilla item
          base-amount: 1
          increase-per-level: 1
        - type: "MMOITEMS"
          item-types: "MATERIAL" # MMOItem Type of the material
          id: "DRAGON_SCALE"
          base-amount: 5
          increase-per-level: 2
```

---

## 📄 License

This plugin is released under the [MIT License](https://opensource.org/licenses/MIT).
