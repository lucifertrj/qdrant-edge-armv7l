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

Install the prebuilt wheel directly from GitHub:

```bash
pip install https://github.com/lucifertrj/qdrant-edge-armv7l/raw/main/qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl
```

Or clone this repo and install the wheel from the checked-out source:

```bash
git clone https://github.com/lucifertrj/qdrant-edge-armv7l.git
cd qdrant-edge-armv7l
pip install ./qdrant_edge_py-0.7.2-cp311-cp311-manylinux_2_28_armv7l.whl
```

## Verify

```bash
python - <<'PY'
from qdrant_edge import EdgeShard

print("qdrant-edge-py import works")
print(EdgeShard)
PY
```

## Notes

- Use this only for 32-bit `armv7l` Raspberry Pi environments.
- If you are on a 64-bit Raspberry Pi OS, prefer the official PyPI package where possible.
- The wheel must match your Python ABI. This file is for CPython 3.11.
