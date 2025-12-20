# Computational Theory Assessment

This repository contains a single Jupyter notebook, [problems.ipynb](problems.ipynb), implementing and testing components used in SHA-256, along with short explanations and references.

Primary standard used throughout:
- NIST FIPS PUB 180-4 (Secure Hash Standard): https://csrc.nist.gov/publications/detail/fips/180/4/final

## Environment

- Python 3.12+ (developed/tested with Python 3.12.1)
- Python dependencies are listed in [requirements.txt](requirements.txt).

Install dependencies:
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Running the Notebook

You can run the notebook in VS Code (recommended) or from the terminal.

VS Code:
- Install the VS Code Jupyter extension.
- Open [problems.ipynb](problems.ipynb).
- Run cells from top to bottom (Kernel → Restart & Run All) to reproduce results.

Terminal:
```bash
python -m pip install -r requirements.txt
jupyter notebook
```
Then open [problems.ipynb](problems.ipynb) in the browser UI and run all cells.

Notes:
- Some cells print values for inspection; others use assertions to test correctness at important boundaries.
- The SHA-256 implementation is validated against Python's reference implementation (`hashlib.sha256`).

## Wordlist File (Problem 5)

Problem 5 performs a dictionary/brute-force attack using a newline-delimited password list.

- The notebook expects a file named [passwords.txt](passwords.txt) in the repository root.
- Format: **one candidate password per line** (text, UTF-8).
- The cracking code hashes each candidate once with SHA-256 and compares the hex digest to the given targets.

## Contents

- Problem 1: 32-bit word operations used by SHA-256 (ROTR, SHR, Ch, Maj, Σ/σ functions).
- Problem 2: Derivation of SHA-256 round constants $K[0..63]$ from fractional cube roots of primes (per the standard).
- Problem 3: SHA-256 padding + parsing into 512-bit blocks.
- Problem 4: SHA-256 compression function (hash state update per 512-bit block).
- Problem 5: Password cracking via dictionary/brute-force over a common-password wordlist, and discussion of how to improve password hashing.

Repository structure:
- [problems.ipynb](problems.ipynb): main submission notebook.
- [passwords.txt](passwords.txt): wordlist used for Problem 5.
- [requirements.txt](requirements.txt): Python dependencies.
- [README.md](README.md): setup and navigation.

## References

References are placed where they are used inside the notebook (per assessment guidance). Key sources include:

- NIST FIPS PUB 180-4 (Secure Hash Standard): https://csrc.nist.gov/publications/detail/fips/180/4/final
  - Used for the official definitions of padding/parsing, constants, and the SHA-256 compression algorithm.
- NumPy scalar types (`numpy.uint32`): https://numpy.org/doc/stable/reference/arrays.scalars.html#numpy.uint32
  - Used to enforce 32-bit wraparound semantics (mod $2^{32}$) for SHA-256 word operations.
- Python `hashlib` documentation: https://docs.python.org/3/library/hashlib.html
  - Used only to verify the notebook’s SHA-256 output against a known-good reference implementation.

Additional reference used in Problem 5:
- OWASP Password Storage Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
  - Used for best-practice guidance on salting and password hashing/KDF choices.