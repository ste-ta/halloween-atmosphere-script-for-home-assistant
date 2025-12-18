# 🎄🎃🎆 Holiday Atmosphere Scripts for Home Assistant

A collection of three specialized Home Assistant scripts that create various festive lighting effects for different holidays. Each script is optimized for reliability with older smart bulbs.

---

## 📦 Available Scripts

### 🎃 Halloween Atmosphere
Creates spooky Halloween lighting effects

### 🎄 Christmas Atmosphere
Creates warm and festive Christmas lighting effects

### 🎆 New Year Atmosphere
Creates celebratory New Year's Eve lighting effects

---

## ✨ Features

- **Dedicated Effects**: Each script contains holiday-specific lighting effects
- **Smart Bulb Optimized**: Special handling for older Philips Hue bulbs that prevents freezing and unavailability
- **Individual Light Control**: Each light gets random variations for organic, lifelike effects
- **Restart Mode**: Automatically stops previous effect when starting a new one
- **Error Tolerant**: Continues running even if individual lights fail to respond
- **XY Color Space**: Uses Zigbee-compatible XY color space for better reliability

---

## 🎬 Available Effects by Holiday

### 🎃 Halloween Effects

**Hell (Fire)** - Flickering red and orange flames with varying intensities
- Colors: Pure red, red-orange, orange, dark red
- Brightness: 100-255 (variable)
- Transition: 2-4 seconds (smooth)

**Lightning** - Dramatic white flashes with darkness in between, staggered across lights
- Colors: White flashes, dark blue ambient
- Brightness: 3-10 (darkness), 255 (flash)
- Transition: Instant flashes

**Graveyard** - Slow, creeping green-blue fog effects with very low brightness
- Colors: Muted poison green, dark teal, fog blue, moss green
- Brightness: 30-60 (very dark)
- Transition: 5-10 seconds (very slow)

**Halloween (Classic)** - Classic Halloween colors with dynamic transitions
- Colors: Pumpkin orange, purple, dark purple, poison green, lime green
- Brightness: 150-220 (bright and festive)
- Transition: 3-6 seconds (smooth)

**Blood Pulse** - Deep red heartbeat rhythm with double pulse (LUB-DUB) then darkness
- Colors: Dark red, blood red, crimson
- Brightness: 5-200 (wide range for dramatic pulse)
- Transition: Rhythmic (heartbeat pattern)

**Stop** - Resets all lights to previous state with smooth 1-second transition

### 🎄 Christmas Effects

Perfect for cosy evenings – lively but never hectic, designed for relaxing by the fire.

**Xmas Tree** - Slow multicolor Christmas tree lights (red, green, white)
- Colors: Red, green, white with warm tones
- Brightness: 110-180 (warm and inviting)
- Transition: 2 seconds
- Cycle: 7-11 seconds between colors

**Xmas Snowfall** - Lively blue and white snowfall effect
- Colors: Various blues and cool whites (includes white for brightness)
- Brightness: 50-135 (more dynamic and lively)
- Transitions: 2-4 seconds (faster, more energetic)
- Pattern: Each light dances independently with staggered timing
- Color hold: 2-3 seconds between changes (quicker shifts)
- Cycle: 1-2 second breaks between updates (more frequent)
- Perfect for: Active, playful winter atmosphere

**Xmas Candlelight** - Warm orange candlelight with subtle, barely-noticeable flickering
- Colors: Deep golden orange tones (more saturated)
- Brightness: 75-90 normal, 70-82 subtle shadow dips (very minimal)
- Transitions: 0.08s shadow flick down, 0.1s recovery (organic)
- Pattern: Each light flickers independently at different random times
- Flicker interval: 1.8-3.8 seconds (long pauses between gentle dips)
- Shadow intensity: Only 5-10 brightness points (barely perceptible, like real candles)

**Xmas Fireplace** - Realistic warm fireplace glow with organic flame movement
- Colors: Deep warm orange/amber (0.55, 0.39 with variations)
- Brightness: 100-180 (warm, cozy fireplace glow)
- Transitions: 2-4 seconds (smooth, natural flame drift)
- Pattern: Each light moves independently like real fire
- Color variation: Random warm color shifts throughout the orange spectrum
- Cycle: 2-4 second color hold, then shifts organically
- Perfect for: Cosy evenings, ambient fireplace vibe

**Xmas Gift Pulse** - Gentle pulsing multicolor effect like festive presents
- Colors: Red, green, white
- Brightness: Soft pulse from 80-190 (gentle, not aggressive)
- Transition: 1.5 seconds per pulse
- Cycle: 4-7 seconds between colors

**Xmas Santa** - Calm red, white, and green Santa-inspired effect
- Colors: Red (Santa suit), white (snow/beard), green (Christmas tree)
- Brightness: 100-160 (cosy and warm)
- Transition: 5-8 seconds (very peaceful)
- Cycle: 8-12 seconds

**Xmas Party** - Synchronized dance party optimized for older Philips Hue bulbs
- Colors: Red, green, white (classic Christmas colors)
- Brightness: 255 full flashes, 100-150 glow between beats
- **Hue-Safe Timing**: 100ms per bulb command + 300ms pauses between color changes (prevents freezing)
- Continuously cycles through 4 party modes, 8 beats each:
  - **Random Color Strobe**: Each beat flashes random Christmas color at 255, dims to 150
  - **Three-Color Cycle**: Red → Green → White cycling with recovery pauses
  - **Red Strobe**: Intense red flashing with Hue-safe delays
  - **Dark Solo Spotlight**: Each light flashes individually (255) with long recovery pauses
- 1-second pause between mode changes (allows bulbs to recover)
- Fully compatible with older Philips Hue bulbs without freezing
- Perfect for: Party mode without overwhelming older Zigbee hardware

**Stop** - Restores lights to previous state with smooth 2-second transition

### 🎆 New Year Effects

**Nye Countdown** - Accelerating white flash countdown effect
- Colors: White flashes
- Brightness: 255 (flash), 5 (darkness)
- Timing: Increasingly rapid flashes

**Nye Confetti** - Rapidly changing multicolor confetti effect
- Colors: Red, blue, purple, white, warm white
- Brightness: 200-255 (bright and celebratory)
- Transition: Instant changes

**Nye Midnight Flash** - Bright flash at midnight with smooth fade
- Colors: Bright white
- Brightness: 255 (initial), 120 (fade)
- Transition: 4 seconds (smooth fade-down)

**Nye Sparkler** - High-variation sparkling white effect
- Colors: White with large variations
- Brightness: 180-255 (bright sparkles)
- Transition: Instant

**Nye Champagne** - Warm golden champagne bubble effect
- Colors: Warm amber/golden tones
- Brightness: 30-140 (gentle celebration)
- Transition: 2-6 seconds

**Stop** - Restores lights to previous state with smooth 1-second transition

---

## 📋 Installation

### Prerequisites
- Home Assistant instance
- RGB-capable smart lights (Philips Hue, WLED, etc.)
- Lights must support `light.turn_on` service with `xy_color` and `brightness`

### Step 1: Add the Scripts

**Option A: Via UI (Recommended)**
1. Go to **Settings** → **Automations & Scenes** → **Scripts**
2. Click **Create Script** (bottom right)
3. Click the **⋮** menu (top right) → **Edit in YAML**
4. Paste the script code for the holiday you want
5. Click **Save**

Repeat for each holiday script you want to install.

**Option B: Via Configuration File**
1. Open your `scripts.yaml` file (or create one if it doesn't exist)
2. Add each script with the appropriate identifier:
   ```yaml
   halloween_atmosphere:
     alias: "🎃 Halloween Atmosphere"
     # ... Halloween script content

   christmas_atmosphere:
     alias: "🎄 Christmas Atmosphere"
     # ... Christmas script content

   newyear_atmosphere:
     alias: "🎆 New Year Atmosphere"
     # ... New Year script content
   ```
3. Add to `configuration.yaml` if not already present:
   ```yaml
   script: !include scripts.yaml
   ```
4. Restart Home Assistant

---

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
2. Select the appropriate script (`script.halloween_atmosphere`, `script.christmas_atmosphere`, or `script.newyear_atmosphere`)
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

---

## 🔧 Customization

### Adjusting Effect Speed

Find the delay values in the effect and modify:

```yaml
# Faster (reduce delays)
- delay:
    seconds: "{{ range(2, 4) | random }}"  # Instead of range(4, 7)

# Slower (increase delays)
- delay:
    seconds: "{{ range(6, 10) | random }}"  # Instead of range(4, 7)
```

### Adding Custom Colors

Locate the `colors:` section or `base_xy:` in any effect and add your XY coordinates:

```yaml
colors:
  - - 0.7006  # X coordinate (red)
    - 0.2993  # Y coordinate
  - - 0.2138  # X coordinate (green)
    - 0.7097  # Y coordinate
```

### Adjusting Brightness Range

Modify the `brightness_levels:` array or `range()` functions:

```yaml
brightness_levels:
  - 255  # Maximum
  - 200
  - 150
  - 100  # Minimum
```

### Creating a New Effect

Copy an existing effect block in any script and modify:

```yaml
# Add to the choose: section
- conditions:
    - condition: template
      value_template: "{{ effect == 'your_effect_name' }}"
  sequence:
    # Your custom effect logic here
```

Don't forget to add your effect name to the selector options at the top!

---

## 📊 Performance Notes

- **CPU Usage**: Minimal - scripts run in background
- **Network Traffic**: Optimized for Zigbee networks with proper delays
- **Recommended Lights Per Call**: Up to 10 lights (more may cause delays on older hubs)
- **Effect Cycle Time**: 3-14 seconds depending on effect and randomization

---

## 🔄 Compatibility

- **Home Assistant**: 2023.x and newer
- **Lights**: Any RGB lights supporting `light.turn_on` with `xy_color` and `brightness`
- **Protocols**: Zigbee (recommended for Hue), Z-Wave, WiFi
- **Bulbs**: 
  - ✅ **Philips Hue** (original & newer models)
  - ✅ WLED
  - ✅ IKEA Tradfri
  - ✅ Dresden Elektronik
  - ✅ Any Zigbee RGB device

---

## 🤝 Contributing

Found a bug or want to add a new effect? Feel free to:
1. Open an issue describing the problem or suggestion
2. Fork the repository and create a pull request
3. Share your custom effects in discussions

---

## 📝 Version History

### v2.0.0 (2025)
- Split combined script into three dedicated holiday scripts
- Improved organization and maintainability
- Each script optimized for its specific holiday

### v1.0.0 (2025)
- Initial release
- 5 Halloween effects: Hell, Lightning, Graveyard, Halloween, Blood, Stop
- 5 Christmas effects: Xmas Twinkle, Xmas Tree, Xmas Snowfall, Xmas Candlelight, Xmas Gift Pulse, Stop
- 5 New Year effects: NYE Countdown, NYE Confetti, NYE Midnight Flash, NYE Sparkler, NYE Champagne, Stop
- Optimized for older Philips Hue bulbs
- Full error handling and recovery

---

## ⚠️ Disclaimer

These scripts control your smart lights rapidly and with various colors/brightness levels. While optimized for reliability:

- Test with a small number of lights first
- Some very old bulbs may still have issues
- Not responsible for any hardware issues (though none are expected)
- May cause photosensitive reactions - use caution

---

## 📜 License

These projects are provided as-is for personal and commercial use. Feel free to modify and redistribute.

---

## 🎃🎄🎆 Happy Holidays!

Created with 💀🎅✨ for the Home Assistant community.
