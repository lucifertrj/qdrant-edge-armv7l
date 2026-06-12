# qdrant-edge armv7l

This repo hosts a prebuilt `qdrant-edge-py` wheel for 32-bit Raspberry Pi Linux.

PyPI currently publishes `qdrant-edge-py` wheels for common desktop/server platforms and Linux ARM64, but not for 32-bit Raspberry Pi `armv7l`. This wheel is built for a Raspberry Pi running 32-bit Linux with Python 3.11.

## Files

```text
qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl
qdrant-edge-python/
```

The wheel is the installable artifact. The `qdrant-edge-python/` directory contains the Qdrant Edge Python binding source used for reference.

Important: `qdrant-edge-python/` is copied from the Qdrant workspace and is not a standalone source build by itself. Its Rust `Cargo.toml` depends on sibling Qdrant workspace crates such as `bm25`, `edge`, `segment`, `shard`, and `sparse`. Use the wheel below for installation from this repo.

Target environment:

```text
Architecture: armv7l
OS: 32-bit Raspberry Pi Linux
Python: CPython 3.11
Package: qdrant-edge-py 0.7.2
```

## Install from GitHub

Check the target device before installing:

```bash
python -V
uname -m
ldd --version | head -n 1
```

Expected:

```text
Python 3.11.x
armv7l
glibc 2.28 or newer
```

Install the prebuilt wheel directly from GitHub:

```bash
pip install https://github.com/lucifertrj/qdrant-edge-armv7l/raw/main/qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl
```

Or clone this repo and install the wheel from the checked-out source:

```bash
git clone https://github.com/lucifertrj/qdrant-edge-armv7l.git
cd qdrant-edge-armv7l
```

> Create an environment variable and Install qdrant-edge

```bash
python3.11 -m venv env
source env/bin/activate
pip install ./qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl
```

## Verify by running an example

```bash
python qdrant-edge-python/examples/mmr-query.py
```

or

```bash
python qdrant-edge-python/examples/bm25-search.py
```

<img width="1920" height="1000" alt="IMG_0703" src="https://github.com/user-attachments/assets/d803a174-008c-454d-a39f-64cad40e6630" />

## Notes

- Use this only for 32-bit `armv7l` Raspberry Pi environments.
- If you are on a 64-bit Raspberry Pi OS, prefer the official PyPI package where possible.
- The wheel must match your Python ABI. This file is for CPython 3.11.

## Troubleshooting

If `pip` prints this error:

```text
ERROR: qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl is not a supported wheel on this platform.
```

It usually means one of these does not match:

- The machine is not Linux `armv7l`.
- Python is not CPython 3.11.
- The system glibc is older than `2.28`.

This error is expected on macOS, x86-64 Linux, ARM64 Linux, or any Python version other than CPython 3.11.
