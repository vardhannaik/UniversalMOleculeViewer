# Contributing to Universal Molecular Visualizer

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

## 🤝 How to Contribute

### Reporting Bugs

If you find a bug, please create an issue with:
- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Browser and OS information
- Screenshots if applicable

### Suggesting Features

Feature requests are welcome! Please:
- Check existing issues first
- Describe the feature clearly
- Explain the use case
- Consider implementation complexity

### Pull Requests

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make your changes**
   - Follow the code style
   - Add comments for complex logic
   - Test thoroughly
4. **Commit with clear messages**
   ```bash
   git commit -m "Add amazing feature"
   ```
5. **Push to your fork**
   ```bash
   git push origin feature/amazing-feature
   ```
6. **Open a Pull Request**

## 📝 Code Style

### JavaScript
- Use ES6+ features
- Prefer `const` over `let`
- Use descriptive variable names
- Add JSDoc comments for functions
- Keep functions focused and small

### HTML/CSS
- Use semantic HTML
- Maintain consistent indentation (4 spaces)
- Keep CSS organized by component
- Use meaningful class names

### Example
```javascript
/**
 * Calculate bond length between two atoms
 * @param {Object} atom1 - First atom with x, y, z coordinates
 * @param {Object} atom2 - Second atom with x, y, z coordinates
 * @returns {number} Bond length in Angstroms
 */
function calculateBondLength(atom1, atom2) {
    const dx = atom2.x - atom1.x;
    const dy = atom2.y - atom1.y;
    const dz = atom2.z - atom1.z;
    return Math.sqrt(dx*dx + dy*dy + dz*dz);
}
```

## 🧪 Testing

Before submitting:
1. Test in multiple browsers (Chrome, Firefox, Safari, Edge)
2. Test with various molecule sizes
3. Check console for errors
4. Verify all features still work
5. Test on mobile devices if UI changes

## 📚 Documentation

- Update README.md for new features
- Add examples to docs/ folder
- Document new file formats
- Update API documentation

## 🎯 Priority Areas

We especially welcome contributions in:

### High Priority
- [ ] Advanced SMILES parser with ring detection
- [ ] PDB file format support
- [ ] Export functionality (PNG, SVG, OBJ)
- [ ] Performance optimizations for large molecules
- [ ] Mobile responsiveness improvements

### Medium Priority
- [ ] Energy minimization algorithms
- [ ] Molecular dynamics animation
- [ ] Additional measurement tools
- [ ] Electrostatic surface visualization
- [ ] Improved bond angle detection

### Low Priority
- [ ] Theme customization
- [ ] Molecule library/database
- [ ] VR/AR support
- [ ] Integration with external APIs

## 🐛 Bug Fixes

Bug fixes are always welcome! Focus on:
- Rendering issues
- Incorrect bond detection
- Performance problems
- Cross-browser compatibility
- Mobile issues

## 💡 Ideas for Contributions

### New File Formats
- MOL/SDF format
- CIF (Crystallographic Information File)
- PQR (Protein with charge)
- PDBQT (AutoDock format)

### Visualization Features
- Stick models
- Ball-and-stick hybrid
- Surface rendering
- Ribbon diagrams for proteins
- Hydrogen bonding visualization

### Analysis Tools
- RMSD calculation
- Molecular weight calculator
- Center of mass
- Gyration radius
- Solvent accessible surface area

### User Interface
- Drag-and-drop file upload
- Better mobile controls
- Keyboard shortcuts
- Command palette
- Measurement mode

## 🔍 Code Review Process

Pull requests will be reviewed for:
- Code quality and style
- Functionality and correctness
- Performance impact
- Documentation
- Test coverage
- Breaking changes

## 📧 Communication

- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General questions and ideas
- **Pull Request Comments**: Code-specific feedback

## 🎓 Learning Resources

New to molecular visualization? Check out:
- [Three.js Documentation](https://threejs.org/docs/)
- [RDKit Documentation](https://www.rdkit.org/docs/)
- [PubChem](https://pubchem.ncbi.nlm.nih.gov/)
- [Protein Data Bank](https://www.rcsb.org/)

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

## 🙏 Thank You!

Every contribution, no matter how small, is valued and appreciated. Together we can build the best open-source molecular visualizer!

---

Questions? Feel free to open an issue or discussion!
