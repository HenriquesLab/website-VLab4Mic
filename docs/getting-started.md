# Getting Started

VLab4Mic is compatible with **Python 3.10, 3.11, 3.12, and 3.13** on macOS, Windows, and Linux.

---

## Step 1 — Create and Activate a Virtual Environment

!!! tip
    We recommend installing VLab4Mic in a dedicated virtual environment to avoid dependency conflicts. The examples below use Python's built-in `venv`; pyenv or Conda can also be used as alternatives.

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## Step 2 — Install VLab4Mic

**For Python scripts only:**

```bash
pip install vlab4mic
```

**Including Jupyter notebook support:**

```bash
pip install vlab4mic vlab4micjupyter
```

On first use, VLab4Mic may download required PDB/CIF structure files. These
runtime files are stored in your user folder at `~/.vlab4mic/structures`, not in
the installed Python package directory. Set `VLAB4MIC_STRUCTURE_DIR` to use a
different cache location.

---

## Verify Installation

Check that VLab4Mic is installed correctly:

```python
import vlab4mic
print(vlab4mic.__version__)
```

Or run a minimal simulation:

```python
from vlab4mic.experiments import image_vsample

images, noiseless, experiment = image_vsample(run_simulation=True)
print("Installation successful!")
```

---

## Next Steps

<div class="grid cards" markdown>

-   :material-notebook:{ .lg .middle } **Use Jupyter Notebooks**

    ---

    Run VLab4Mic without writing code in Google Colab or a local Jupyter Lab.

    [Notebooks guide →](notebooks.md)

-   :material-code-braces:{ .lg .middle } **Use Python Scripts**

    ---

    Run VLab4Mic from the command line or a Python interpreter.

    [Python usage guide →](python-usage.md)

</div>
