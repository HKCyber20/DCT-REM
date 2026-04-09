# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a LaTeX research paper on DCT-based visual servoing for photoacoustic (PA) imaging. The paper describes a hybrid 6-DoF dual-sensor servoing framework using DCT features and Intel RealSense depth cameras for robotic medical imaging.

## Document Versions

The repository contains multiple versions of the same paper:

- **main.tex** - English version (primary document)
- **cn2.tex** - Chinese version with ctex package
- **cni.tex** - Chinese version variant
- **rev_mengdi.tex** - Chinese revision version

All versions share the same structure and reference the same bibliography (`references.bib`) and figures in `graph/`.

## Building the Documents

### Compile English version:
```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

### Compile Chinese versions:
Chinese versions require XeLaTeX or LuaLaTeX due to the ctex package:
```bash
xelatex cn2.tex
bibtex cn2
xelatex cn2.tex
xelatex cn2.tex
```

Replace `cn2.tex` with `cni.tex` or `rev_mengdi.tex` as needed.

### Using latexmk (if available):
```bash
latexmk -pdf main.tex
latexmk -xelatex cn2.tex
```

## Document Structure

The paper follows this organization:

1. **Section 1**: DCT-Based Servo Control Algorithm Design
   - Subsection 1.1: Spectral Feature Representation
   - Subsection 1.2: PA-Optimized Interaction Matrix Construction
   - Subsection 1.3: Adaptive Control Law for Vascular Surveillance
   - Subsection 1.4: Dual-Sensor Hybrid 6-DoF Servoing Framework

## Key LaTeX Packages and Dependencies

### Critical Package Loading Order
The document uses a specific package loading sequence to avoid conflicts:
1. `xcolor` must load before cleveref
2. `natbib` hook is disabled with `\let\NAT@parse\undefined`
3. `hyperref` loads before `cleveref`
4. `cleveref` uses `[capitalize]` option with custom color styling

### Custom Commands
- `\cmark`, `\xmark` - checkmark and cross symbols (pifont)
- `\fstar`, `\hstar` - filled and hollow stars
- Custom column type `C{width}` for centered paragraphs
- Custom colors: `labelblue` and `numberblue` (RGB 0,0,180)

### Chinese Support
Chinese versions use `\usepackage[UTF8]{ctex}` which requires XeLaTeX or LuaLaTeX compilation.

## References and Figures

- **Bibliography**: `references.bib` (IEEE style with natbib)
- **Figures**: Located in `graph/` directory
  - `IDCT_new.png` - DCT transformation visualization
  - `spatial calibration.png` - Feature construction methodology
  - `feature matrix.jpg` - Feature matrix visualization

## Cross-References

The document uses cleveref for intelligent cross-referencing with custom formatting:
- Equations: `\cref{eq:label}` → "Equation. (1)" in blue
- Figures: `\cref{fig:label}` → "Fig. 1" in blue
- Tables: `\cref{tab:label}` → "Table. 1" in blue
- Algorithms: `\cref{algorithm:label}` → "Algorithm. 1" in blue
