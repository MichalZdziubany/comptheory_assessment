# Computational Theory Assessment

This repository contains a Jupyter notebook implementing components used in SHA-256 and related exercises.

## Environment

Python 3.12.1
See `requirements.txt` for Python package dependencies.

Install dependencies:
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Running the Notebook

Open in VS Code and use the Jupyter extension, or from terminal, or use github codespaces:
```bash
python -m pip install -r requirements.txt
jupyter notebook
```
Then open `problems.ipynb` and run all cells in order (Kernel → Restart & Run All).

## Contents

Problem 1: 32-bit word operations used by SHA-256 (ROTR, SHR, Ch, Maj, Σ/σ functions).
Problem 2: Fractional parts of cube roots (constants).
Problem 3: SHA-256 padding.
Problem 4: Hashes
Problem 5: Passwords

## References

FIPS PUB 180-4: Secure Hash Standard (SHS) 
https://csrc.nist.gov/publications/detail/fips/180/4/final