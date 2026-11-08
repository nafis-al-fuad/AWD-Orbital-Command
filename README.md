# 🛰️ AWD Orbital Command

**AWD MESH | ORBITAL COMMAND V4.0** — A futuristic real-time agricultural monitoring dashboard powered by MQTT data streaming and cutting-edge WebGL visualizations.

**Live Demo:** [https://awd-orbital-command.pages.dev/](https://awd-orbital-command.pages.dev/)

---

## Overview

AWD Orbital Command is an advanced web-based control center designed to monitor agricultural irrigation systems in real-time. It provides a sleek, cyberpunk-inspired interface for tracking soil moisture, water levels, and gate status across multiple farming sectors. The application connects to MQTT brokers to stream live sensor data and displays it through immersive 3D visualizations and interactive HUD cards.

### Key Features

✨ **Real-Time MQTT Integration**
- Dual broker support (EMQX & HiveMQ)
- Live sensor data streaming
- Packet loss monitoring

🎨 **Immersive UI Design**
- Cyberpunk aesthetic with glassmorphism effects
- 3D isometric sector visualization with mouse tilt parallax
- Animated particle effects and scanning effects
- Smooth transitions and micro-interactions

📊 **Data Visualization**
- Live water level metrics with 3D volume representation
- Soil saturation percentage tracking
- Interactive sparkline graphs
- Gate status indicators

🔌 **Multi-Platform Support**
- Responsive design (Desktop & Mobile)
- GitHub Pages deployment ready
- WebSocket support for secure connections

---

## Project Structure

```
AWD-Orbital-Command/
├── index.html          # Main application (single-file)
├── LICENSE             # Apache 2.0 License
└── README.md           # This file
```

---

## Quick Start

### Access the Application

The application is hosted online. Simply visit:

[https://awd-orbital-command.pages.dev/](https://awd-orbital-command.pages.dev/)

No installation or build process required—just open in your browser!

### Deploy Your Own

1. **Fork this repository** or clone it:
   ```bash
   git clone https://github.com/nafis-al-fuad/AWD-Orbital-Command.git
   cd AWD-Orbital-Command
   ```

2. **Enable GitHub Pages**:
   - Go to Settings → Pages
   - Select `main` branch as source
   - Your deployment will be available at `https://<your-username>.github.io/AWD-Orbital-Command/`

3. **Modify MQTT Configuration** (optional):
   - Edit the `CONFIG` object in `index.html` to change broker settings or topic

---

## Configuration

### MQTT Settings

The application connects to MQTT brokers to receive sensor data. Configuration is defined in the `CONFIG` object:

```javascript
const CONFIG = {
    topic: "awd_project/bibartan26/data",     // MQTT topic to subscribe to
    emqx: { 
        host: "broker.emqx.io", 
        port: 8084,                           // WebSocket Secure (WSS)
        name: "EMQX", 
        color: "#00f3ff",                     // Primary theme color
        sec: "#00ff9d",                       // Secondary theme color
        glow: "rgba(0, 243, 255, 0.3)"       // Glow effect
    },
    hive: { 
        host: "broker.hivemq.com", 
        port: 8884,                           // WebSocket Secure (WSS)
        name: "HIVE", 
        color: "#bc13fe", 
        sec: "#ffaa00", 
        glow: "rgba(188, 19, 254, 0.3)" 
    },
    dry: 3500,     // Sensor value for dry soil
    wet: 1000,     // Sensor value for wet soil
    maxW: 2000,    // Max water sensor reading
    maxCm: 10      // Max water depth in cm
};
```

### Expected MQTT Message Format

The application expects JSON messages with the following structure:

```json
{
  "w1": 1500,      // Water level for Sector 01 (0-2000)
  "w2": 1800,      // Water level for Sector 02 (0-2000)
  "s1": 2800,      // Soil saturation for Sector 01 (1000-3500)
  "s2": 3200,      // Soil saturation for Sector 02 (1000-3500)
  "g1": 1,         // Gate status for Sector 01 (0=closed, 1=open)
  "g2": 0          // Gate status for Sector 02 (0=closed, 1=open)
}
```

---

## UI Components

### Header
- **System Title**: "AWD PRIME ORBITAL COMMAND"
- **Packet Loss Monitor**: Real-time packet count display
- **Broker Toggle**: Switch between EMQX (cyan) and HiveMQ (purple) brokers
- **System Exit**: Navigation link

### Main Visualization
- **Isometric Map**: 3D rendered sectors with mouse-tracking parallax
- **Water Volumes**: Dynamic 3D representations showing current water levels
- **Interactive Links**: Visual connections between HUD cards and map sectors

### HUD Cards (Right Panel)
Two data cards for Sector 01 and Sector 02, each displaying:
- Location coordinates
- Sector name and status
- Water level (cm)
- Soil saturation percentage (%)
- Real-time sparkline graph
- Gate status indicator

### Footer
- **System Log Ticker**: Continuous scrolling log of system events

---

## Interactions

### Mouse Hover Effects
- **Sector 3D Boxes**: Hover to see 3D depth effect
- **HUD Cards**: Hover to draw animated connection lines to corresponding sectors
- **Header Elements**: Hover effects on broker toggle and exit button

### Theme Switching
- Click the **BROKER_TOGGLE** switch to change between EMQX (cyan) and HiveMQ (purple) themes
- Triggers a glitch effect and reconnects to the new broker
- Colors update across all UI elements

### Mobile Responsiveness
- Isometric view scales down on smaller screens
- Touch-friendly layout with stacked components
- Simplified animations for better performance

---

## Technologies Used

<table>
  <tr>
    <td align="center" width="33%"><strong>Frontend</strong><br><br><img src="https://img.shields.io/badge/HTML5-Document%20structure-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5"><br><img src="https://img.shields.io/badge/CSS3-Responsive%20UI-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3"><br><img src="https://img.shields.io/badge/JavaScript-Interactive%20dashboard-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript"></td>
    <td align="center" width="33%"><strong>Live Data</strong><br><br><img src="https://img.shields.io/badge/MQTT-Paho%20client-660066?style=for-the-badge" alt="MQTT with Paho client"><br><img src="https://img.shields.io/badge/WebSockets-Secure%20live%20stream-4353FF?style=for-the-badge" alt="WebSockets"><br><img src="https://img.shields.io/badge/Google%20Fonts-Inter%20%2B%20JetBrains%20Mono-4285F4?style=for-the-badge&logo=googlefonts&logoColor=white" alt="Google Fonts"></td>
    <td align="center" width="33%"><strong>Visualization</strong><br><br><img src="https://img.shields.io/badge/Canvas-Particle%20effects-000000?style=for-the-badge" alt="Canvas API"><br><img src="https://img.shields.io/badge/SVG-Sparklines%20%26%20links-FFB13B?style=for-the-badge&logo=svg&logoColor=white" alt="SVG"><br><img src="https://img.shields.io/badge/CSS-3D%20transforms-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS 3D transforms"></td>
  </tr>
</table>

### Libraries & APIs
- **MQTT**: [Paho MQTT Client](https://cdnjs.cloudflare.com/ajax/libs/paho-mqtt/1.0.1/mqttws31.min.js)
- **Fonts**: [Google Fonts](https://fonts.googleapis.com) (Inter, JetBrains Mono)
- **Canvas API**: For particle effects
- **SVG**: For connection lines and sparkline graphs
- **CSS 3D Transforms**: For isometric visualization

### Browser Support
- Modern browsers with support for:
  - CSS Grid & Flexbox
  - CSS 3D Transforms
  - Canvas
  - WebSockets
  - ES6 JavaScript

---

## Visual Effects

### Animations
- **Boot Sequence**: Animated hexagon loader with terminal logs
- **Glitch Effect**: Chromatic aberration on broker switch
- **Scan Wipe**: Horizontal sweep effect on state changes
- **Particle System**: Floating background particles
- **Scanline Bar**: CRT-style scanning animation
- **Ticker**: Scrolling system log

### Styling
- **Glassmorphism**: Frosted glass cards with backdrop blur
- **Neon Colors**: Cyan (#00f3ff), Green (#00ff9d), Orange (#ffaa00), Red (#ff003c)
- **Vignette Effect**: Darkened edges for depth
- **Grid Floor**: 3D perspective grid background

---

## Customization

### Change Colors
Edit the CSS variables in the `<style>` section:

```css
:root {
    --theme-primary: #00f3ff;    /* Primary accent color */
    --theme-secondary: #00ff9d;  /* Secondary accent color */
    --theme-warn: #ffaa00;       /* Warning/caution color */
    --theme-danger: #ff003c;     /* Error/danger color */
    --theme-glow: rgba(0, 243, 255, 0.3);  /* Glow effect */
}
```

### Change Sector Names
Edit the sector titles in the HTML:

```html
<!-- Look for lines like: -->
<div class="card-title">SECTOR 01 // PADDY</div>
<div class="card-title">SECTOR 02 // WHEAT</div>
```

### Modify Sensor Calibration
Adjust the `CONFIG` values to match your sensor specifications:

```javascript
dry: 3500,     // Adjust based on dry soil reading
wet: 1000,     // Adjust based on wet soil reading
maxW: 2000,    // Max water sensor value
maxCm: 10      // Max water depth to display
```

---

## Browser Console Logs

The application logs system events to the footer ticker. Watch for messages like:
- `[SYSTEM] BOOT SEQUENCE COMPLETE`
- `[NET] MESH TOPOLOGY MAPPED`
- `[IO] SENSORS ONLINE`
- `[MESH] NODE_04 SYNCED`
- `[UPLINK ESTABLISHED: EMQX/HIVE]`

---

## License

This project is licensed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for details.

---

## Credits

**Created by**: [DaRk77NesS](https://github.com/DaRk77NesS)

**MQTT Brokers**:
- [EMQX](https://broker.emqx.io) - Open source MQTT broker
- [HiveMQ](https://broker.hivemq.com) - Reliable MQTT hosting

---

## Support & Contributions

- 🐛 **Found a bug?** Open an issue
- 💡 **Have an idea?** Submit a feature request
- 🔗 **Want to contribute?** Pull requests are welcome!

---

## Tips for Best Experience

✅ Use a modern browser (Chrome, Firefox, Safari, Edge)
✅ For live data, ensure your MQTT broker is publishing to the configured topic
✅ Desktop view recommended for full 3D parallax effect
✅ Keep network stable for uninterrupted data streaming

---

**Version**: 4.0 | **Last Updated**: January 2026
