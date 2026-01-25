# Claude Assistant Guide

This document provides setup instructions and troubleshooting guidance for working with this Statistical Rethinking notes project.

## Project Overview

This is a Quarto-based documentation project containing notes, exercises, and homework solutions for Richard McElreath's Statistical Rethinking course. The project uses:
- **Quarto** for rendering notebooks
- **R 4.5.2** for R code chunks (managed by `rig` and `rv`)
- **Python** for Python code chunks (using venv)
- **Hunspell** for spellchecking

## Repository Structure

```
.
├── book-notes/          # Notes and exercises from textbook
├── course-notes/        # Notes from lectures and slides
├── homework/            # Homework solutions
├── _site/               # Generated HTML output
├── .venv/               # Python virtual environment
├── rv/                  # R package management (rv)
├── rproject.toml        # R project configuration
├── rv.lock              # R dependency lock file
├── requirements.txt     # Python dependencies
└── _quarto.yml          # Quarto configuration
```

## Environment Setup

### Prerequisites Check

Before rendering, verify:
1. Quarto is installed
2. R 4.5.2 is installed and available
3. Python virtual environment exists at `.venv/`
4. Hunspell is installed (for spellcheck)

### R Environment Setup

**Check installed R versions:**
```bash
rig list
```

**Install R 4.5.2 (if needed):**
```bash
rig add 4.5.2
```

**Set as default:**
```bash
rig default 4.5.2
```

**Sync R packages:**
```bash
rv sync
```

The R environment is managed by `rv` and configured in `rproject.toml`. The `.Rprofile` automatically activates the rv environment when R starts.

### Python Environment Setup

**Activate the virtual environment:**

On Windows (Git Bash/MSYS):
```bash
source .venv/Scripts/activate
```

On Windows (PowerShell):
```powershell
.venv\Scripts\Activate.ps1
```

On macOS/Linux:
```bash
source .venv/bin/activate
```

**Verify Python packages are installed:**
```bash
pip list | grep matplotlib
```

If packages are missing, install from requirements.txt:
```bash
pip install -r requirements.txt
```

## Rendering Workflow

### Render a Single Document

**On Windows (Git Bash):**
```bash
export PATH="/c/Program Files/R/R-4.5.2/bin/x64:$PATH"
source .venv/Scripts/activate
quarto render course-notes/lecture-02.qmd
```

**On macOS/Linux:**
```bash
export PATH="/usr/local/lib/R/4.5.2/bin:$PATH"  # Adjust path as needed
source .venv/bin/activate
quarto render course-notes/lecture-02.qmd
```

### Preview Entire Site

```bash
# Ensure both R and Python environments are set up first
quarto preview
```

## Common Issues and Solutions

### Issue: R Version Mismatch

**Symptom:**
```
WARNING: R version specified in config (4.5.2) does not match session version (4.4.3).
rv library will not be activated until the issue is resolved. Entering safe mode...
```

**Solution:**
1. Install R 4.5.2: `rig add 4.5.2`
2. Set as default: `rig default 4.5.2`
3. Update PATH in current shell (see rendering workflow above)
4. Verify: `R --version` should show 4.5.2

### Issue: Missing Python Packages (e.g., matplotlib)

**Symptom:**
```
ModuleNotFoundError: No module named 'matplotlib'
```

**Solution:**
1. Activate venv: `source .venv/Scripts/activate` (Windows) or `source .venv/bin/activate` (macOS/Linux)
2. Verify packages: `pip list`
3. Install if needed: `pip install -r requirements.txt`

### Issue: Matplotlib Object Output in Rendered HTML

**Symptom:**
Rendered output shows object representations like:
```
<matplotlib.lines.Line2D object at 0x...>
Text(0.5, 1.0, 'W')
```

**Solution:**
Add semicolons to suppress return values in Python code chunks:
```python
axes[i].set_title(label);     # Note the semicolon
axes[i].set_xlabel("p");
axes[i].set_ylabel("Density");
```

Alternatively, use Quarto directive:
```python
#| output: false
# ... code that generates unwanted output ...
```

### Issue: Missing R Packages

**Symptom:**
```
Error in loadNamespace(x) : there is no package called 'rmarkdown'
```

**Solution:**
1. Ensure R 4.5.2 is active
2. Run: `rv sync`
3. Verify packages installed: Check `rv.lock` for expected packages

## Important Notes

1. **Always activate both environments** before rendering:
   - Set correct R version in PATH
   - Activate Python venv

2. **R package management**:
   - Packages are defined in `rproject.toml`
   - Lock file is `rv.lock`
   - Use `rv sync` to install/update
   - `.Rprofile` handles automatic activation

3. **Python package management**:
   - Packages are defined in `requirements.txt`
   - Use pip within activated venv
   - Reticulate (R package) bridges R and Python

4. **Rendering behavior**:
   - Quarto uses the R executable found in PATH
   - R then loads the rv environment via `.Rprofile`
   - R's reticulate package manages Python integration
   - Python venv must be activated before Quarto starts

## Quick Reference Commands

```bash
# Check R version
R --version

# List installed R versions
rig list

# Check rv environment status
rv info

# Activate Python venv (Windows Git Bash)
source .venv/Scripts/activate

# Activate Python venv (macOS/Linux)
source .venv/bin/activate

# Render single file
quarto render path/to/file.qmd

# Preview entire site
quarto preview

# Sync R packages
rv sync
```

## Key Files to Check When Troubleshooting

1. `rproject.toml` - R version and package requirements
2. `rv.lock` - Locked R package versions
3. `.Rprofile` - R startup script (activates rv)
4. `requirements.txt` - Python package requirements
5. `_quarto.yml` - Quarto configuration
