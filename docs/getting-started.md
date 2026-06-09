# Getting Started

Choose the option that best suits your needs:

| Option | Skills Needed | Best For |
|--------|---------------|----------|
| **[1. Google Colab](#option-1-google-colab)** | None | Beginners, teaching, quick experiments |
| **[2. LabConstrictor Desktop App](#option-2-labconstructor-desktop-app)** | None | One-click local install, no Python required |
| **[3. Local Jupyter Notebooks](#option-3-local-jupyter-notebooks)** | Basic installation | Smooth widget-based use |
| **[4. Python Scripts](#option-4-python-scripts)** | Comfortable with code | Full flexibility & automation |

---

## Option 1 — Google Colab

The easiest way to start — no installation, no configuration, works entirely in the browser.

✔ No installation  
✔ No configuration  
✔ Works in browser  
✔ Always up to date  

| Category | Description | Notebook | Colab |
|---------|-------------|----------|-------|
| **Main Interface** | Create virtual samples & simulate imaging | [Notebook](https://github.com/HenriquesLab/VLab4Mic/blob/main/notebooks/VLab4Mic_main.ipynb) | [Open in Colab](https://githubtocolab.com/HenriquesLab/VLab4Mic/blob/main/notebooks/VLab4Mic_main.ipynb) |
| **Parameter Sweeps** | Configure & run simulation sweeps | [Notebook](https://github.com/HenriquesLab/VLab4Mic/blob/main/notebooks/VLab4Mic_parameter_sweeps.ipynb) | [Open in Colab](https://githubtocolab.com/HenriquesLab/VLab4Mic/blob/main/notebooks/VLab4Mic_parameter_sweeps.ipynb) |

!!! tip
    If the Colab link fails, download the `.ipynb` file from the Notebook column and upload it via **File → Upload notebook** in Google Colab.

---

## Option 2 — LabConstrictor Desktop App

The easiest way to run VLab4Mic **locally** — no Python, no conda, no terminal.

!!! tip
    Recommended for users who want a ready-to-run desktop application without managing Python environments.

✔ One-click installer for Windows & macOS  
✔ No Python or environment setup required  
✔ Notebooks bundled and ready to run  
✔ Automatic version checks  

**Download and install:**  
Follow the instructions at [https://github.com/HenriquesLab/LabConstrictor-VLab4Mic/blob/main/.tools/docs/download_executable.md](https://github.com/HenriquesLab/LabConstrictor-VLab4Mic/blob/main/.tools/docs/download_executable.md)

Powered by [LabConstrictor](https://github.com/CellMigrationLab/LabConstrictor) — a CI/CD-based pipeline that packages Jupyter notebooks into installable desktop applications ([Hidalgo-Cenalmor et al., 2026](https://arxiv.org/abs/2603.10704)).

---

## Option 3 — Local Jupyter Notebooks

VLab4Mic is compatible with **Python 3.10, 3.11, 3.12, and 3.13** on macOS, Windows, and Linux.

### Step 1 — Create and Activate a Virtual Environment

!!! tip
    We recommend installing VLab4Mic in a dedicated virtual environment to avoid dependency conflicts. The examples below use Python's built-in `venv`; pyenv or Conda can also be used as alternatives.

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 2 — Install VLab4Mic with Jupyter support

```bash
pip install vlab4mic "vlab4micjupyter[local]"
```

On first use, VLab4Mic may download required PDB/CIF structure files. These
runtime files are stored in your user folder at `~/.vlab4mic/structures`, not in
the installed Python package directory. Set `VLAB4MIC_STRUCTURE_DIR` to use a
different cache location.

### Step 3 — Launch Jupyter Lab

```bash
jupyter lab
```

Then download and open the notebooks from:  
[https://github.com/HenriquesLab/VLab4Mic/tree/main/notebooks](https://github.com/HenriquesLab/VLab4Mic/tree/main/notebooks)

---

## Option 4 — Python Scripts

For full flexibility and automation from the command line or a Python interpreter.

### Step 1 — Create and Activate a Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 2 — Install VLab4Mic

```bash
pip install vlab4mic
```

### Step 3 — Run a simulation

```python
from vlab4mic.experiments import image_vsample
import matplotlib.pyplot as plt

modalities = ["Widefield", "Confocal", "STED"]

images, noiseless, experiment = image_vsample(
    structure="7R5K",
    probe_template="Antibody",
    probe_target_type="Sequence",
    probe_target_value="ELAVGSL",
    multimodal=modalities,
    number_of_particles=10,
    run_simulation=True,
)

fig, axs = plt.subplots(1, len(modalities))
for i, mod in enumerate(modalities):
    axs[i].imshow(images[mod][0], cmap="magma")
    axs[i].set_title(mod)
plt.show()
```

For more examples see the [Python usage guide](python-usage.md).

---

## Verify Installation

Check that VLab4Mic is installed correctly:

```python
import vlab4mic
from importlib.metadata import version

print("VLab4Mic", version("vlab4mic"))
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

-   :material-google:{ .lg .middle } **Google Colab**

    ---

    Run VLab4Mic in the browser with no installation.

    [Open notebooks →](notebooks.md)

-   :material-monitor-arrow-down:{ .lg .middle } **LabConstrictor Desktop App**

    ---

    One-click installable app for Windows & macOS. No Python required.

    [Download →](https://github.com/HenriquesLab/LabConstrictor-VLab4Mic/blob/main/.tools/docs/download_executable.md)

-   :material-notebook:{ .lg .middle } **Use Jupyter Notebooks**

    ---

    Run VLab4Mic without writing code in a local Jupyter Lab.

    [Notebooks guide →](notebooks.md)

-   :material-code-braces:{ .lg .middle } **Use Python Scripts**

    ---

    Run VLab4Mic from the command line or a Python interpreter.

    [Python usage guide →](python-usage.md)

</div>
