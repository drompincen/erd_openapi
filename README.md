# OpenAPI ER Diagram Visualizer

A client-side web tool that transforms OpenAPI 3.x JSON specifications into interactive Entity-Relationship diagrams. This application runs entirely in the browser with no backend required, ensuring your API specifications never leave your machine.

## Features

**Schema Visualization**: Automatically detects and displays relationships between schemas including inheritance (allOf), one-to-one, one-to-many, and many-to-many relationships.

**Interactive Diagrams**: Pan, zoom, and drag nodes to arrange diagrams for optimal comprehension. Node positions persist across re-renders, allowing iterative refinement of your diagram layout.

**Export Capability**: Generate SVG diagrams for inclusion in technical documentation.

**Schema Selection**: Use the dual-list interface to select specific schemas to visualize, filtering out irrelevant portions of large API specifications.

**Zero Installation**: Runs entirely in the browser as a single HTML file with embedded CSS and JavaScript. No build step required.

## Getting Started

### Running Locally

You can run the application in one of two ways:

1. **Direct file access**: Open `index.html` directly in a web browser

2. **Local HTTP server**: Start a simple HTTP server and navigate to the URL:
   ```bash
   python3 -m http.server 8000
   ```
   Then visit http://localhost:8000

### Usage

1. Paste your OpenAPI JSON specification into the left panel (or click "Load Sample" to try with demo data)
2. The application parses the `components.schemas` section automatically
3. Select which schemas to visualize using the dual-list interface (Available/Visible lists)
4. Click "Render" or press `Ctrl/Cmd+Enter` to generate the ER diagram
5. Drag nodes to rearrange the layout as needed
6. Use the export button to download the diagram as SVG

## Relationship Types

The visualizer detects and displays four types of relationships:

| Type | Detection | Visual |
|------|-----------|--------|
| Inheritance | `allOf` composition | Triangle arrowhead |
| One-to-One | Direct `$ref` property | Bar markers at both ends |
| One-to-Many | Array of `$ref` items | Bar at one end, crow's foot at many end |
| Many-to-Many | Bidirectional array references | Crow's feet at both ends |

## Dependencies

The application uses the following external libraries (loaded via CDN):

- [D3.js](https://d3js.org/) - Data visualization and DOM manipulation
- [Dagre-D3](https://github.com/dagrejs/dagre-d3) - Graph layout and rendering
- [SVG-Pan-Zoom](https://github.com/bumbu/svg-pan-zoom) - Pan and zoom functionality for SVG diagrams

## Privacy

All processing happens client-side. Your API specifications are never sent to any server, making this tool safe for use with sensitive or proprietary API definitions.

## License

MIT License
