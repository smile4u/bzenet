# Build
## 1. Clone repo
```sh
git clone https://github.com/smile4u/bzenet bzenet
cd bzenet
```
## 2. Download latest enet lib and unpack it into `enet/` dir.
```sh
git clone --branch v1.3.14 https://github.com/lsalzman/enet
```
## 3. Apply patches from `patches` folder.
```sh
git apply .\patches\01.patch_bze-14386.diff
```
## 4. Build package

Requirements: python with pip and venv

Prepare venv
```sh
python -m venv .venv
.venv\Scripts\python.exe -m pip install setuptools cython twine build
```

Build package
```sh
.venv\Scripts\python.exe -m build
```

# Publish
```sh
.venv\Scripts\python.exe -m twine upload dist/*
```

# Test
```sh
.venv\Scripts\python.exe -m pip install -e .
.venv\Scripts\python.exe test_enet.py
```

