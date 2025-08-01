# LFVXD: Lepton Flavor Violating X Decays

A Python library for symbolic and numerical calculations of Lepton Flavor Violating (LFV) particle decays, including Higgs bosons, Z bosons, and Seesaw neutrino models.

## Overview

LFVXD provides tools for theoretical physics calculations involving:

- **Lepton Flavor Violating Higgs Decays (LFVHD)**: Symbolic computation of form factors and decay rates
- **Z Boson LFV Decays**: Calculations for processes like Z → μe, Z → τμ, etc.
- **Seesaw Neutrino Models**: Implementation of Type-I, Inverse, and Left-Right seesaw mechanisms
- **Passarino-Veltman Functions**: Standard loop integrals used in quantum field theory
- **One-Loop Diagrams**: Symbolic representation of triangle and bubble topologies

## Key Features

- **Symbolic Mathematics**: Built on SymPy for exact symbolic calculations
- **Numerical Evaluation**: High-precision numerical implementations using mpmath
- **Modular Design**: Separate modules for different physics scenarios
- **Jupyter Integration**: Example notebooks demonstrating usage
- **Form Factor Calculations**: Complete one-loop form factors for LFV processes

## Installation

### Prerequisites

- Python 3.7+
- SymPy
- SciPy  
- NumPy
- mpmath (for numerical evaluations)

### From Source

```bash
git clone https://github.com/moiseszeleny/LFVXD.git
cd LFVXD
```

## Project Structure

```
LFVXD/
├── PaVe.py              # Passarino-Veltman functions (symbolic)
├── PaVe2.py             # Extended PaVe functions  
├── vertexes.py          # Vertex definitions (SSS, SFF, etc.)
├── topologias.py        # Loop diagram topologies
├── Higgs/               # Higgs boson LFV decay functions
├── Zboson/              # Z boson LFV decay functions  
├── SeeSaw/              # Seesaw neutrino model implementations
├── numeric/             # Numerical evaluation routines
├── Examples/            # Jupyter notebook examples
└── *.ipynb              # Various calculation examples
```

## Basic Usage

### Passarino-Veltman Functions

```python
from LFVXD.PaVe import A0, B0, C0
from sympy import symbols

# Define masses
m1, m2, m3 = symbols('m1 m2 m3', positive=True)
p2 = symbols('p2')

# Scalar one-point function
a0 = A0(m1)

# Scalar two-point function  
b0 = B0(p2, m1, m2)

# Scalar three-point function
c0 = C0(p2, m1, m2, m3)
```

### Vertex Definitions

```python
from LFVXD.vertexes import VertexSSS
from sympy import symbols

# Define coupling constant
g = symbols('g')

# Three-scalar vertex
vertex = VertexSSS(g)
coupling = vertex.show()  # Returns g
```

### LFV Higgs Decay Example

```python
from LFVXD.Higgs.functionsFS import GFS
from sympy import symbols

# Define particle masses
ma, mb, M0, M1 = symbols('ma mb M0 M1', positive=True)

# Calculate form factor component
ff_component1 = GFS(ma, mb, M0, M1, component=1)
```

## Physics Background

### Lepton Flavor Violation

In the Standard Model with massless neutrinos, lepton flavor is conserved. However, neutrino oscillations demonstrate that lepton flavor is violated in nature. This library calculates LFV processes that could be observable in:

- Higgs boson decays: h → μe, h → τμ, h → τe
- Z boson decays: Z → ℓᵢℓⱼ (i ≠ j)
- Charged lepton decays: μ → eγ, τ → μγ, etc.

### Passarino-Veltman Functions

These are standard one-loop integrals in dimensional regularization:

- **A₀**: Tadpole integrals
- **B₀, B₁**: Two-point functions (propagator corrections)
- **C₀, C₁, C₂**: Three-point functions (vertex corrections)

### Seesaw Mechanisms

The library implements several seesaw models for neutrino mass generation:

- **Type-I Seesaw**: Right-handed neutrino extension
- **Inverse Seesaw**: Pseudo-Dirac neutrino structure  
- **Left-Right Seesaw**: Left-right symmetric models

## Examples

Explore the Jupyter notebooks in the repository:

- `test.ipynb`: Basic PaVe function usage
- `testFF_H.ipynb`: Higgs form factor calculations
- `testFF_Z.ipynb`: Z boson form factor calculations
- `ISS_eigenvasl.ipynb`: Inverse seesaw eigenvalue analysis
- `SeeSaw/test_SS.ipynb`: Standard seesaw model examples

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## Author

**Moises Zeleny**  
Email: moiseszeleny@gmail.com

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## Citation

If you use this code in your research, please cite:

```
Zeleny, M. (2024). LFVXD: A Python Library for Lepton Flavor Violating X Decays. 
GitHub repository: https://github.com/moiseszeleny/LFVXD
```

## References

- Passarino, G., & Veltman, M. J. G. (1979). One-loop corrections for e⁺e⁻ annihilation into μ⁺μ⁻ in the Weinberg model. Nuclear Physics B, 160(1), 151-207.
- For physics references related to specific calculations, see the individual module documentation and example notebooks.