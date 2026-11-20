# ALDRA Python Environment

## Supported runtime

- Python 3.10 or newer
- Google Colab for the current Android-first development workflow
- Local development can use a virtual environment

## Dependencies

Install the project dependencies with:

```bash
python -m pip install -r requirements.txt
```

The dependency list covers:
- NumPy and Pandas: dataset loading and manipulation
- scikit-learn: TF-IDF vectorization and evaluation metrics
- PyTorch: the ALDRA MLP classifier
- Matplotlib: training and evaluation plots
- tqdm: visible progress indicators
- pytest: automated tests

## Google Colab setup

1. Create a new notebook and select a Python runtime.
2. Check the runtime and installed core libraries:

```python
import sys
import numpy
import pandas
import sklearn
import torch

print("Python:", sys.version)
print("NumPy:", numpy.__version__)
print("Pandas:", pandas.__version__)
print("scikit-learn:", sklearn.__version__)
print("PyTorch:", torch.__version__)
print("CUDA available:", torch.cuda.is_available())
```

3. Install the remaining project dependencies. Colab commonly includes PyTorch already, so do not reinstall it unnecessarily:

```python
%pip install "numpy>=1.26,<3.0" "pandas>=2.1,<4.0" "scikit-learn>=1.4,<2.0" "matplotlib>=3.8,<4.0" "tqdm>=4.66,<5.0" "pytest>=8.0,<10.0"
```

4. If PyTorch is missing, install it using the official PyTorch installation selector for the runtime's operating system and accelerator: https://pytorch.org/get-started/locally/

## Local setup

### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### Windows PowerShell

```powershell
py -3 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Environment verification

After installation, run:

```bash
python -c "import numpy, pandas, sklearn, torch, matplotlib, tqdm, pytest; print('ALDRA environment OK'); print('PyTorch:', torch.__version__); print('CUDA available:', torch.cuda.is_available())"
```

CUDA is optional. The prediction-only classifier can be developed and tested on CPU.

## Reproducibility notes

- Record the Python and dependency versions in experiment reports.
- Do not commit virtual environments, secrets, datasets containing private information, or model checkpoints.
- Keep the existing ALDRA classifier architecture unchanged during environment setup.
- Dependency ranges provide compatibility bounds; exact versions should be recorded when an experiment is run.
