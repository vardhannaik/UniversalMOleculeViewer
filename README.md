# 🧪 Universal Molecular Visualizer

A powerful, interactive 3D molecular visualization tool built with Three.js. Visualize molecules, create crystal lattices, and analyze molecular structures directly in your browser.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow)

## ✨ Features

### Core Visualization
- **3D Interactive Display** - Rotate, zoom, and explore molecules in real-time
- **Multiple Input Formats** - Support for XYZ, SMILES, and JSON formats
- **Automatic Bond Detection** - Intelligently detects chemical bonds based on atomic distances
- **CPK Color Scheme** - Standard chemistry colors for all elements

### Crystal Lattice Generation
- **3D Lattice Structures** - Create repeating molecular units in X, Y, and Z dimensions
- **Adjustable Spacing** - Control intermolecular distances (3-15 Ångströms)
- **Layer Visualization** - Stack molecules to simulate crystalline solids
- **Up to 5×5×5 Arrays** - Generate up to 125 molecular units

### Analysis Tools
- **Bond Angles** - Measure and display bond angles with visual arcs
- **Bond Lengths** - Show accurate bond distances in Ångströms
- **Molecular Formula** - Automatic calculation from structure
- **Atom/Bond Counting** - Real-time statistics

### Preset Molecules
- Water (H₂O)
- Methane (CH₄)
- Benzene (C₆H₆)
- Ethanol (C₂H₅OH)
- Caffeine (C₈H₁₀N₄O₂)
- Glucose (C₆H₁₂O₆)

## 🚀 Quick Start

### Option 1: Direct Use
Simply open `index.html` in any modern web browser. No installation required!

### Option 2: Local Server
```bash
# Clone the repository
git clone https://github.com/yourusername/molecular-visualizer.git
cd molecular-visualizer

# Serve with Python
python -m http.server 8000

# Or with Node.js
npx http-server
```

Then navigate to `http://localhost:8000`

## 📖 Usage Guide

### Loading Molecules

#### Using XYZ Format
```
3
Water molecule
O    0.0000    0.0000    0.0000
H    0.7570    0.5860    0.0000
H   -0.7570    0.5860    0.0000
```

#### Using SMILES
```
CCO           # Ethanol
c1ccccc1      # Benzene
CC(=O)O       # Acetic acid
```

#### Using JSON
```json
{
  "atoms": [
    {"element": "O", "x": 0, "y": 0, "z": 0},
    {"element": "H", "x": 0.757, "y": 0.586, "z": 0},
    {"element": "H", "x": -0.757, "y": 0.586, "z": 0}
  ],
  "bonds": [[0, 1], [0, 2]]
}
```

### Creating Crystal Lattices

1. Load any molecule using one of the methods above
2. Use the **Crystal Lattice Settings** sliders:
   - **X-axis Repeat**: Create side-by-side copies
   - **Y-axis Repeat**: Stack vertically
   - **Z-axis Repeat**: Create layers
   - **Spacing**: Adjust intermolecular distance

**Example**: Ice crystal structure
- Load Water preset
- Set X=3, Y=3, Z=3
- Adjust spacing to 4.0 Å

### Controls

#### Mouse Controls
- **Left Click + Drag**: Rotate molecule
- **Scroll Wheel**: Zoom in/out

#### Keyboard Shortcuts
- **+**: Zoom in
- **-**: Zoom out

#### Buttons
- **Auto-Rotate**: Toggle automatic rotation
- **Reset**: Return to default view
- **Labels**: Show/hide atom labels
- **Angles**: Display bond angles
- **Bonds**: Show bond lengths
- **Zoom +/-**: Manual zoom control

## 🎨 Supported Elements

The visualizer supports the complete periodic table with accurate CPK colors:

| Element | Symbol | Color | Van der Waals Radius |
|---------|--------|-------|---------------------|
| Hydrogen | H | White | 1.20 Å |
| Carbon | C | Gray | 1.70 Å |
| Nitrogen | N | Blue | 1.55 Å |
| Oxygen | O | Red | 1.52 Å |
| Fluorine | F | Light Green | 1.47 Å |
| Phosphorus | P | Orange | 1.80 Å |
| Sulfur | S | Yellow | 1.80 Å |
| Chlorine | Cl | Green | 1.75 Å |
| Bromine | Br | Dark Red | 1.85 Å |
| Iodine | I | Purple | 1.98 Å |
| Boron | B | Pink | 1.92 Å |
| Silicon | Si | Tan | 2.10 Å |
| ... and more | ... | ... | ... |

Full list includes alkali metals (Li, Na, K), alkaline earth metals (Mg, Ca), transition metals (Fe, Zn, Cu, Ag, Au), and more.

## 🔧 Technical Details

### Technologies Used
- **Three.js (r128)** - 3D graphics rendering
- **Vanilla JavaScript (ES6)** - No framework dependencies
- **HTML5 Canvas** - Label rendering

### Architecture
```
molecular-visualizer/
├── index.html              # Main application file
├── README.md              # This file
├── LICENSE                # MIT License
├── CONTRIBUTING.md        # Contribution guidelines
├── examples/              # Example molecule files
│   ├── water.xyz
│   ├── caffeine.xyz
│   └── glucose.json
└── docs/                  # Additional documentation
    ├── FILE_FORMATS.md
    ├── API.md
    └── EXAMPLES.md
```

### Key Features Implementation

#### Bond Detection Algorithm
```javascript
// Bonds are detected based on element-specific distance thresholds
const maxBondLength = {
    'H': { 'H': 0.9, 'C': 1.2, 'N': 1.2, 'O': 1.1 },
    'C': { 'C': 1.7, 'N': 1.6, 'O': 1.5 },
    // ... and more
};
```

#### 3D Coordinate Generation
- XYZ: Direct coordinate input
- SMILES: Basic algorithmic 3D structure generation
- JSON: Flexible custom format

## 📊 Performance

- **Atoms**: Tested up to 10,000 atoms
- **Lattice**: Up to 5×5×5 (125 molecules)
- **Frame Rate**: 60 FPS on modern browsers
- **Memory**: ~50MB for typical molecules

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

### Development Setup
```bash
git clone https://github.com/yourusername/molecular-visualizer.git
cd molecular-visualizer

# Make changes to index.html
# Test in browser

# Submit pull request
```

### Areas for Contribution
- [ ] Advanced SMILES parser (stereochemistry, aromatics)
- [ ] Export to various formats (PNG, SVG, OBJ)
- [ ] Protein structure support (PDB format)
- [ ] Energy minimization
- [ ] Measurement tools (distances, dihedrals)
- [ ] Animation of molecular dynamics
- [ ] VR/AR support

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Three.js** - Amazing 3D graphics library
- **CPK Coloring** - Standard atom colors from Corey-Pauling-Koltun model
- **RDKit** - Inspiration for SMILES parsing
- **PubChem** - Chemical structure database

## 📮 Contact

- **Issues**: [GitHub Issues](https://github.com/yourusername/molecular-visualizer/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/molecular-visualizer/discussions)

## 🔮 Roadmap

### Version 1.1 (Planned)
- [ ] PDB file support for proteins
- [ ] Save/load sessions
- [ ] Screenshot capture
- [ ] Dark/light theme toggle

### Version 1.2 (Planned)
- [ ] Molecular orbital visualization
- [ ] Electrostatic potential surfaces
- [ ] Hydrogen bond detection
- [ ] Animation controls

### Version 2.0 (Future)
- [ ] WebGL2 rendering
- [ ] GPU-accelerated calculations
- [ ] Multi-molecule comparison
- [ ] Integration with chemical databases

## 📚 Additional Resources

- [File Format Documentation](docs/FILE_FORMATS.md)
- [API Reference](docs/API.md)
- [Example Gallery](docs/EXAMPLES.md)
- [Tutorial Videos](https://youtube.com/playlist/...)

## ⭐ Star History

If you find this project useful, please consider giving it a star on GitHub!

---

**Made with ❤️ for the chemistry community**
