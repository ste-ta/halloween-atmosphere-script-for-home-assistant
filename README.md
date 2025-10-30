# 🎃 Halloween Atmosphere Script for Home Assistant

A comprehensive Home Assistant script that creates various spooky lighting effects for Halloween. Optimized for reliability with older smart bulbs.

---

**Script Parameters:**
- `lights` (required): Single entity ID or list of light entity IDs
- `effect` (required): One of: `hell`, `lightning`, `graveyard`, `halloween`,`blood`, `stop`

**Compatibility:**
- Home Assistant 2023.x and newer
- Any RGB lights supporting `light.turn_on` with `rgb_color` and `brightness`


## ✨ Features

- **6 Different Effects**: Hell (fire), Lightning (storm), Graveyard (fog),Blood, Halloween (classic colors), and Stop
- **Smart Bulb Optimized**: Special handling for older Philips Hue bulbs that prevents freezing and unavailability
- **Individual Light Control**: Each light gets random variations for organic, lifelike effects
- **Restart Mode**: Automatically stops previous effect when starting a new one
- **Error Tolerant**: Continues running even if individual lights fail to respond

## 🎬 Available Effects

### 🔥 Hell
Flickering red and orange flames with varying intensities.
- **Colors**: Pure red, red-orange, orange, dark red
- **Brightness**: 100-255 (variable)
- **Transition**: 2-4 seconds (smooth)
- **Perfect for**: Demonic themes, fire simulations

### ⚡ Lightning
Dramatic white flashes with darkness in between, staggered across lights like real lightning.
- **Colors**: White flashes, dark blue ambient
- **Brightness**: 3-10 (darkness), 255 (flash)
- **Transition**: Instant flashes
- **Perfect for**: Storm effects, dramatic moments

### 🪦 Graveyard
Slow, creeping green-blue fog effects with very low brightness.
- **Colors**: Muted poison green, dark teal, fog blue, moss green
- **Brightness**: 30-60 (very dark)
- **Transition**: 5-10 seconds (very slow)
- **Perfect for**: Eerie atmosphere, haunted house vibes

### 🩸 Blood Pulse
Deep red heartbeat rhythm - double pulse (LUB-DUB) then darkness.

- **Colors**: Dark red, blood red, crimson
- **Brightness** 5-200 (wide range for dramatic pulse)
- **Transition** Rhythmic (heartbeat pattern)
- **Perfect for**: Vampire themes, horror scenes, dramatic effect, heartbeat sound sync

### 🎃 Halloween
Classic Halloween colors with dynamic transitions.
- **Colors**: Pumpkin orange, purple, dark purple, poison green, lime green
- **Brightness**: 150-220 (bright and festive)
- **Transition**: 3-6 seconds (smooth)
- **Perfect for**: General Halloween decoration, party mode

### 🛑 Stop
Resets all lights to warm white at full brightness with a smooth 2-second transition.

## 📋 Installation

### Prerequisites
- Home Assistant instance
- RGB-capable smart lights (Philips Hue, WLED, etc.)
- Lights must support `light.turn_on` service with `rgb_color` and `brightness`

### Step 1: Add the Script

**Option A: Via UI (Recommended)**
1. Go to **Settings** → **Automations & Scenes** → **Scripts**
2. Click **Add Script** (bottom right)
3. Click the **⋮** menu (top right) → **Edit in YAML**
4. Paste the entire script code
5. Click **Save**

**Option B: Via Configuration File**
1. Open your `scripts.yaml` file (or create one if it doesn't exist)
2. Add the script with the identifier:
   ```yaml
   halloween_atmosphere:
     alias: "🎃 Halloween Atmosphere"
     # ... rest of the script
   ```
3. Add to `configuration.yaml` if not already present:
   ```yaml
   script: !include scripts.yaml
   ```
4. Restart Home Assistant

## 🎮 Usage

### Basic Usage

**Start an effect:**
```yaml
service: script.halloween_atmosphere
data:
  lights:
    - light.living_room
    - light.kitchen
    - light.hallway
  effect: hell
```

**Stop the effect:**
```yaml
service: script.halloween_atmosphere
data:
  lights:
    - light.living_room
    - light.kitchen
    - light.hallway
  effect: stop
```

### Switch Between Effects
Simply call the script again with a different effect - it will automatically stop the current one:

```yaml
service: script.halloween_atmosphere
data:
  lights:
    - light.living_room
  effect: lightning
```

### From the UI
1. Go to **Developer Tools** → **Services**
2. Select `script.halloween_atmosphere`
3. Choose your lights in the **lights** field
4. Select effect in the **effect** dropdown
5. Click **Call Service**

### In Automations
```yaml
automation:
  - alias: "Halloween Evening Effect"
    trigger:
      - platform: sun
        event: sunset
    action:
      - service: script.halloween_atmosphere
        data:
          lights:
            - light.living_room
            - light.dining_room
          effect: graveyard
```

### With Dashboard Buttons
```yaml
type: button
name: "🔥 Hell Fire"
tap_action:
  action: call-service
  service: script.halloween_atmosphere
  data:
    lights:
      - light.living_room
    effect: hell
```

## 🔧 Customization

### Adjusting Effect Speed

Find the delay values in each effect and modify:

```yaml
# Faster (reduce delays)
- delay:
    seconds: "{{ range(2, 4) | random }}"  # Instead of range(4, 7)

# Slower (increase delays)
- delay:
    seconds: "{{ range(6, 10) | random }}"  # Instead of range(4, 7)
```

### Adding Custom Colors

Locate the `colors:` section in any effect and add your RGB values:

```yaml
colors:
  - [255, 0, 0]      # Red
  - [0, 255, 0]      # Green
  - [0, 0, 255]      # Blue
  - [255, 255, 0]    # Your custom color
```

### Adjusting Brightness Range

Modify the `brightness_levels:` array:

```yaml
brightness_levels:
  - 255  # Maximum
  - 200
  - 150
  - 100  # Minimum
```

### Creating a New Effect

Copy an existing effect block and modify:

```yaml
# Add to the choose: section
- conditions:
    - condition: template
      value_template: "{{ effekt == 'your_effect_name' }}"
  sequence:
    # Your custom effect logic here
```

Don't forget to add your effect name to the selector options at the top!

## 📊 Performance Notes

- **CPU Usage**: Minimal - script runs in background
- **Network Traffic**: Optimized for Zigbee networks with proper delays
- **Recommended Lights Per Call**: Up to 10 lights (more may cause delays on older hubs)
- **Effect Cycle Time**: 3-14 seconds depending on effect and randomization

## 🤝 Contributing

Found a bug or want to add a new effect? Feel free to:
1. Open an issue describing the problem or suggestion
2. Fork the repository and create a pull request
3. Share your custom effects in discussions

## 📝 Version History

### v1.0.0 (2025)
- Initial release
- 5 effects: Hell, Lightning, Graveyard, Halloween, Stop
- Optimized for older Philips Hue bulbs
- Full error handling and recovery

## ⚠️ Disclaimer

This script controls your smart lights rapidly and with various colors/brightness levels. While optimized for reliability:

- Test with a small number of lights first
- Some very old bulbs may still have issues
- Not responsible for any hardware issues (though none are expected)
- May cause photosensitive reactions - use caution

## 📜 License

This project is provided as-is for personal and commercial use. Feel free to modify and redistribute.

## 🎃 Happy Halloween!

Created with 💀 for the Home Assistant community.

