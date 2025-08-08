## Dunbar's Number – Interactive Visualization

A single-page, interactive visualization that explains Dunbar's Number—the cognitive limit to the number of stable social relationships a human can maintain—through layered networks and simple simulations.

### Why this matters
- **Human limits**: Most people can meaningfully keep up with about 150 people. This shapes how teams, communities, and organizations function.
- **Design implications**: Social platforms, org structures, and community tools benefit from respecting natural group sizes and layers of intimacy.
- **Intuition building**: The layered visualization (5, 15, 50, 150) makes an abstract concept concrete and explorable.

### Features
- **Layered model**: Clickable layers representing 5 (intimates), 15 (close friends), 50 (meaningful ties), 150 (stable relationships).
- **Interactive network**: Randomized network generation with a central “you,” hover effects, and radial layout.
- **Layer highlighting**: Dim or emphasize nodes by layer to see how the network thins as intimacy increases.
- **Live stats**: Displays total visible connections and the currently selected layer.
- **Responsive UI**: Works across desktop and mobile.

### Quick start
No build steps or dependencies.

Option 1: Open the file directly
1. Double-click `index.html` to open it in your browser.

Option 2: Serve locally (recommended for consistent behavior)
```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### How it works
- **Pure HTML/CSS/JS**: No frameworks or external libraries. All logic is embedded in `index.html`.
- **DOM-based drawing**: People are absolutely positioned `<div>` elements (`.person`), and connections are thin `<div>` elements rotated to form lines.
- **Key functions** (in the `<script>` of `index.html`):
  - `generateNetwork()`: Places a central node and four concentric layers with randomized angles/jitter. Creates some center-to-node connections.
  - `createPerson(x, y, className, color)`: Builds a node and attaches hover interactions.
  - `createConnection(x1, y1, x2, y2)`: Computes distance/angle to render a 1px rotated line.
  - `highlightLayer(layerSize)`: Maps 5/15/50/150 to internal layer indices, dims nodes beyond the selected layer, and updates stats.
  - `showAllLayers()`: Resets the view and stats.

#### Layer configuration
Edit the `layers` array in `index.html` to change counts, radii, or colors:
```javascript
const layers = [
  { count: 5,  radius: 60,  color: '#ff6b6b' },
  { count: 10, radius: 120, color: '#4ecdc4' },
  { count: 35, radius: 180, color: '#45b7d1' },
  { count: 100, radius: 240, color: '#96ceb4' }
];
```

To change the label-to-layer mapping used when you click the sidebar layers (5/15/50/150), update the layer map:
```javascript
const layerMap = { 5: 0, 15: 1, 50: 2, 150: 3 };
```

### Usage tips
- Click a layer card (e.g., 15) to highlight nodes up to that intimacy level and see the filtered connection count.
- Click "Generate Network" to randomize node placements and connections.
- Click "Show All Layers" to reset the filters and stats.

### Project structure
- `index.html`: UI, styles, and all interactive logic.
- `README.md`: Project description and usage.
- `LICENSE`: Project license.

### References
- Robin Dunbar’s research and the popularization of Dunbar’s Number: see summaries like the Wikipedia entry for context (search for "Dunbar's Number").

### License
This project is open source. See `LICENSE` for details.
