# Build
1. Clone repo
```
git clone https://github.com/smile4u/bzenet bzenet
cd bzenet
```
2. Download latest enet lib and unpack it into `enet/` dir.
3. Install python modules: 
    - Cython
    - setuptool
    - twine

### Sources
```
python setup.py sdist
twine upload dist/*
```

### Windows prebuild
```
python setup.py build --plat-name=win32 bdist_wheel
python setup.py build --plat-name=win-amd64 bdist_wheel
twine upload dist/*
```

### Linux prebuild
Run docker conrainer: (see https://github.com/pypa/manylinux)
```
docker run -it quay.io/pypa/manylinux2010_x86_64
```
or you can also specify a local dir with `bzenet` that will be available under docker:
```
docker run -it -v /path_to_local/bzenet:/bzenet quay.io/pypa/manylinux2010_x86_64
```
Under docker, install:
```
/opt/python/cp37-cp37m/bin/pip install Cython
/opt/python/cp37-cp37m/bin/pip install twine
```
Under docker, run from cloned `bzenet` folder:
```
cd /bzenet
/opt/python/cp37-cp37m/bin/python3.7 setup.py bdist_wheel
auditwheel repair dist/*
/opt/python/cp37-cp37m/bin/twine upload wheelhouse/*
```

### Mac prebuild
Sources package should be ok for osx.

Or pre-build it with:
```
python setup.py bdist_wheel
twine upload dist/*
```
