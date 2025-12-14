# File Format Documentation

This document describes all supported molecular file formats in the Universal Molecular Visualizer.

## Table of Contents
- [XYZ Format](#xyz-format)
- [SMILES Format](#smiles-format)
- [JSON Format](#json-format)
- [Future Formats](#future-formats)

---

## XYZ Format

### Description
The XYZ format is a simple Cartesian coordinate format commonly used in computational chemistry.

### Structure
```
<number of atoms>
<comment line>
<element> <x> <y> <z>
<element> <x> <y> <z>
...
```

### Example: Water (H₂O)
```
3
Water molecule - optimized geometry
O    0.0000    0.0000    0.0000
H    0.7570    0.5860    0.0000
H   -0.7570    0.5860    0.0000
```

### Example: Methane (CH₄)
```
5
Methane - tetrahedral geometry
C    0.0000    0.0000    0.0000
H    0.6276    0.6276    0.6276
H   -0.6276   -0.6276    0.6276
H   -0.6276    0.6276   -0.6276
H    0.6276   -0.6276   -0.6276
```

### Specifications
- **Coordinates**: Ångströms (Å)
- **Number format**: Decimal (e.g., 1.234)
- **Element symbols**: Standard (H, C, N, O, etc.)
- **Bonds**: Auto-detected based on atomic distances

### Sources
- Computational chemistry software (Gaussian, ORCA, Psi4)
- Molecular editors (Avogadro, Chimera)
- Online databases (PubChem, ChemSpider)

---

## SMILES Format

### Description
SMILES (Simplified Molecular Input Line Entry System) is a line notation for describing molecular structure.

### Basic Syntax
- **Atoms**: Element symbols (C, N, O, etc.)
- **Bonds**: 
  - Single: implicit or `-`
  - Double: `=`
  - Triple: `#`
  - Aromatic: lowercase letters
- **Branches**: Parentheses `()`
- **Rings**: Numbers

### Examples

#### Simple Molecules
```
O              # Water (H₂O)
CC             # Ethane (C₂H₆)
CCO            # Ethanol (C₂H₅OH)
C=O            # Formaldehyde
C#N            # Hydrogen cyanide
```

#### Branched Molecules
```
CC(C)C         # Isobutane
CC(O)C         # Isopropanol
CC(=O)O        # Acetic acid
```

#### Aromatic Compounds
```
c1ccccc1       # Benzene
c1ccccc1O      # Phenol
c1ccccc1C      # Toluene
```

#### Complex Molecules
```
CC(=O)OC1=CC=CC=C1C(=O)O                    # Aspirin
CN1C=NC2=C1C(=O)N(C(=O)N2C)C                # Caffeine
C([C@@H]1[C@H]([C@@H]([C@H](C(O1)O)O)O)O)O  # Glucose
```

### Limitations (Current Implementation)
- Basic parser - handles simple molecules well
- Complex stereochemistry may be simplified
- Ring systems are approximated in 3D
- For publication-quality structures, use XYZ format

### Future Enhancements
- Full stereochemistry support
- Advanced ring perception
- Aromatic bond handling
- Integration with RDKit or similar library

---

## JSON Format

### Description
Custom JSON format for maximum flexibility in defining molecular structures.

### Structure
```json
{
  "atoms": [
    {"element": "C", "x": 0.0, "y": 0.0, "z": 0.0},
    ...
  ],
  "bonds": [[0, 1], [1, 2], ...],
  "metadata": {
    "name": "Molecule Name",
    "formula": "C6H6",
    "source": "computational"
  }
}
```

### Required Fields
- **atoms**: Array of atom objects
  - `element`: Element symbol (string)
  - `x`, `y`, `z`: Coordinates in Ångströms (numbers)
- **bonds**: Array of bond pairs (optional)
  - `[atom1_index, atom2_index]`

### Optional Fields
- **metadata**: Additional information
  - `name`: Molecule name
  - `formula`: Chemical formula
  - `charge`: Total charge
  - `multiplicity`: Spin multiplicity
  - `source`: Data source

### Example: Benzene
```json
{
  "atoms": [
    {"element": "C", "x": 1.2124, "y": 0.7002, "z": 0.0000},
    {"element": "C", "x": 1.2124, "y": -0.7002, "z": 0.0000},
    {"element": "C", "x": 0.0000, "y": -1.4004, "z": 0.0000},
    {"element": "C", "x": -1.2124, "y": -0.7002, "z": 0.0000},
    {"element": "C", "x": -1.2124, "y": 0.7002, "z": 0.0000},
    {"element": "C", "x": 0.0000, "y": 1.4004, "z": 0.0000},
    {"element": "H", "x": 2.1552, "y": 1.2442, "z": 0.0000},
    {"element": "H", "x": 2.1552, "y": -1.2442, "z": 0.0000},
    {"element": "H", "x": 0.0000, "y": -2.4884, "z": 0.0000},
    {"element": "H", "x": -2.1552, "y": -1.2442, "z": 0.0000},
    {"element": "H", "x": -2.1552, "y": 1.2442, "z": 0.0000},
    {"element": "H", "x": 0.0000, "y": 2.4884, "z": 0.0000}
  ],
  "bonds": [
    [0,1], [1,2], [2,3], [3,4], [4,5], [5,0],
    [0,6], [1,7], [2,8], [3,9], [4,10], [5,11]
  ],
  "metadata": {
    "name": "Benzene",
    "formula": "C6H6"
  }
}
```

### Advantages
- Complete control over structure
- Include metadata
- Explicit bond specification
- Easy to generate programmatically
- Human-readable

### Use Cases
- Custom molecular structures
- Programmatic molecule generation
- Converting from other formats
- Including additional data

---

## Future Formats

### Planned Support

#### PDB (Protein Data Bank)
- Standard format for proteins and nucleic acids
- Header information and metadata
- Secondary structure annotation
- Priority: **High**

#### MOL/SDF
- Common in chemical databases
- 2D and 3D coordinates
- Bond order information
- Priority: **High**

#### CIF (Crystallographic Information File)
- Crystallographic data
- Unit cell parameters
- Space group information
- Priority: **Medium**

#### PQR
- PDB with partial charges and radii
- Electrostatics calculations
- Priority: **Medium**

#### PDBQT (AutoDock)
- Molecular docking
- Flexibility information
- Priority: **Low**

---

## Bond Detection Algorithm

When bonds are not explicitly provided (XYZ, SMILES), they are detected based on atomic distances.

### Algorithm
```javascript
for each pair of atoms (i, j):
    distance = sqrt((x2-x1)² + (y2-y1)² + (z2-z1)²)
    
    if distance < threshold(element1, element2):
        create_bond(i, j)
```

### Distance Thresholds (Ångströms)

| Atom Pair | Max Distance |
|-----------|-------------|
| H-H       | 0.9 Å       |
| H-C       | 1.2 Å       |
| H-N       | 1.2 Å       |
| H-O       | 1.1 Å       |
| C-C       | 1.7 Å       |
| C-N       | 1.6 Å       |
| C-O       | 1.5 Å       |
| C-S       | 1.9 Å       |
| N-N       | 1.6 Å       |
| N-O       | 1.5 Å       |
| O-O       | 1.5 Å       |

### Limitations
- Cannot distinguish bond orders
- May miss long-range interactions
- Assumes standard bond lengths

---

## Conversion Tools

### Online Converters
- [OpenBabel](http://openbabel.org/) - Universal converter
- [NCI CADD](https://cactus.nci.nih.gov/) - SMILES converter
- [ChemSpider](http://www.chemspider.com/) - Structure search

### Software
- **Avogadro** - Open-source molecular editor
- **PyMOL** - Molecular visualization
- **VMD** - Visual Molecular Dynamics
- **Chimera** - UCSF visualization tool

### Python Libraries
```python
# Using RDKit to generate XYZ from SMILES
from rdkit import Chem
from rdkit.Chem import AllChem

mol = Chem.MolFromSmiles('CCO')
mol = Chem.AddHs(mol)
AllChem.EmbedMolecule(mol)
Chem.MolToXYZFile(mol, 'ethanol.xyz')
```

---

## Best Practices

### For XYZ Files
1. Include meaningful comment line
2. Use consistent decimal places (4-6)
3. Optimize geometry first
4. Include all hydrogen atoms

### For SMILES
1. Use canonical SMILES when possible
2. Validate with online tools
3. Include stereochemistry for chiral molecules
4. Test with simple molecules first

### For JSON
1. Validate JSON syntax
2. Use consistent coordinate precision
3. Include metadata
4. Specify bonds explicitly when known

---

## Troubleshooting

### Common Issues

**Problem**: Molecule not appearing
- Check file format syntax
- Verify coordinates are not all zero
- Ensure proper element symbols

**Problem**: Incorrect bonds
- Provide explicit bonds (JSON format)
- Check coordinate units (should be Ångströms)
- Verify structure optimization

**Problem**: SMILES parsing errors
- Use simpler SMILES notation
- Validate on ChemSpider
- Try XYZ format instead

---

## Resources

- [XYZ Format Specification](https://en.wikipedia.org/wiki/XYZ_file_format)
- [SMILES Tutorial](http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html)
- [PDB Format Guide](https://www.wwpdb.org/documentation/file-format)
- [JSON Specification](https://www.json.org/)

---

**Last Updated**: December 2024
