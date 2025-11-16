# Interactive 3D Portfolio Scene

A beautiful, interactive 3D workspace scene built with Three.js that showcases creative coding projects. Features a stylized character at a desk with clickable monitors that display project information.

## Features

- **Interactive 3D Scene**: Fully navigable 3D environment with orbital camera controls
- **6 Project Showcases**: Each monitor displays a different project with hover effects
- **Modal System**: Click monitors to view detailed project information
- **Keyboard Navigation**: Full keyboard support (Tab to cycle, Enter to select, Escape to close)
- **Responsive Design**: Works on desktop and tablet devices
- **Smooth Animations**: Idle character animations and smooth transitions
- **Performance Optimized**: Targets 60fps on modern browsers

## Quick Start

### Option 1: Direct Browser

Simply open `portfolio.html` in any modern web browser:

```bash
open portfolio.html
# or
firefox portfolio.html
# or
google-chrome portfolio.html
```

### Option 2: Embed in iframe

Embed the portfolio in any webpage:

```html
<iframe src="portfolio.html" width="100%" height="600px" frameborder="0"></iframe>
```

### Option 3: Local Server

For best results, serve via a local HTTP server:

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js
npx http-server
```

Then visit `http://localhost:8000/portfolio.html`

## Controls

- **Mouse Drag**: Rotate camera around the scene
- **Mouse Wheel**: Zoom in/out
- **Click Monitor**: Open project details
- **Tab**: Cycle through monitors (keyboard navigation)
- **Enter**: Open selected monitor details
- **Escape**: Close modal

## Customization

### Adding/Editing Projects

Edit the `projects` array in `portfolio.html` (around line 295):

```javascript
const projects = [
    {
        id: 1,
        title: "Your Project Name",
        description: "Brief description of your project...",
        technologies: ["Tech1", "Tech2", "Tech3"],
        liveUrl: "https://your-project-url.com",
        thumbnail: "path/to/thumbnail.jpg", // or data URI
        monitorPosition: { x: -3, y: 1.2, z: 0.5 }
    },
    // Add more projects...
];
```

### Customizing Colors

Key color variables to customize:

```javascript
// Background gradient
scene.background = new THREE.Color(0x1a1a2e);

// Accent color (monitor glow, buttons, etc.)
// Search for: 0x00d4ff and replace with your hex color

// Desk color
const deskMaterial = new THREE.MeshStandardMaterial({
    color: 0x4a3728, // Change this
});

// Character colors
const bodyMaterial = new THREE.MeshStandardMaterial({
    color: 0x3a5a7a, // Change this
});
```

### Adjusting Monitor Positions

Monitors are positioned using the `monitorPosition` property:

- **x**: Left (-) to Right (+)
- **y**: Height (typically 1.2 for desk level)
- **z**: Back (-) to Front (+)

Example arc formation:
```javascript
// Far left
monitorPosition: { x: -3, y: 1.2, z: 0.5 }

// Center front
monitorPosition: { x: 0, y: 1.2, z: 1.5 }

// Far right
monitorPosition: { x: 3, y: 1.2, z: 0.5 }
```

### Lighting Adjustments

Modify lighting in the `setupLighting()` function:

```javascript
// Increase overall brightness
const ambientLight = new THREE.AmbientLight(0x404060, 0.8); // Increase from 0.6

// Change accent colors
const accentLight = new THREE.PointLight(0xffaa00, 0.6); // Change color/intensity
```

## Technical Details

- **Three.js Version**: r128 (CDN)
- **File Size**: ~25KB (HTML + inline CSS/JS)
- **Dependencies**: Three.js only (loaded from CDN)
- **Browser Support**: Modern browsers with WebGL support
- **Target Performance**: 60fps

## Project Structure

```
portfolio.html          # Single self-contained file
├── CSS (inline)
│   ├── Loading screen styles
│   ├── Modal/overlay styles
│   └── UI component styles
└── JavaScript (inline)
    ├── Project data array
    ├── Three.js scene setup
    ├── 3D object creation
    ├── Animation system
    ├── Interaction handlers
    └── Modal system
```

## Browser Compatibility

- ✅ Chrome/Edge 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Opera 76+
- ⚠️ Mobile: Limited support (fallback recommended)

## Performance Tips

1. **Reduce Shadow Quality**: Decrease `shadow.mapSize` for better performance
2. **Lower Pixel Ratio**: Set `renderer.setPixelRatio(1)` instead of device pixel ratio
3. **Fewer Monitors**: Reduce number of projects to 4 instead of 6
4. **Disable Fog**: Remove `scene.fog` for slight performance gain

## Troubleshooting

### Scene appears black
- Check browser console for WebGL errors
- Ensure browser supports WebGL
- Try opening in a different browser

### Monitors not clickable
- Ensure mouse events aren't blocked by other elements
- Check browser console for JavaScript errors

### Poor performance
- Reduce number of monitors/projects
- Lower shadow quality settings
- Disable fog and some lights

## License

MIT License - Feel free to use and modify for your portfolio!

## Credits

Built with [Three.js](https://threejs.org/) - JavaScript 3D library
