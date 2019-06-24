# Build
1. Clone repo
```
git clone https://github.com/smile4u/pyenet bzenet
cd bzenet
```
2. Download latest enet lib and unpack it into `enet/` dir.
3. Install python modules: 
    - Cython
    - setuptool
    - twine

### Windows
```
python setup.py bdist_wheel --plat-name=win32
python setup.py bdist_wheel --plat-name=win-amd64
twine upload dist/*
```

### Linux
Run docker conrainer: (see https://github.com/pypa/manylinux)
```
docker -i -t quay.io/pypa/manylinux2010_x86_64
```
Under docker, install:
```
/opt/python/cp37-cp37m/bin/pip install Cython
/opt/python/cp37-cp37m/bin/pip install twine
```
Under docker, run from cloned `bzenet` folder:
```
/opt/python/cp37-cp37m/bin/python3.7 setup.py bdist_wheel
auditwheel repair dist/*
 /opt/python/cp37-cp37m/bin/twine upload wheelhouse/*
```

### Mac
Linux package should be ok for osx.

Or build it:
```
python setup.py bdist_wheel
twine upload dist/*
```
