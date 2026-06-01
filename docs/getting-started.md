# Getting Started

VLab4Mic is compatible with **Python 3.10, 3.11, 3.12, and 3.13** on macOS, Windows, and Linux.

---

## Step 1 — Install VLab4Mic

!!! tip
    We recommend installing VLab4Mic in a dedicated virtual environment to avoid dependency conflicts. You can create one with Conda, pyenv, or Python's built-in `venv`; activate it before running the install command below.

**For Python scripts only:**

```bash
pip install vlab4mic
```

**Including Jupyter notebook support:**

```bash
pip install vlab4mic vlab4micjupyter
```

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
