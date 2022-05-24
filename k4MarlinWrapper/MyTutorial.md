# Mon tutoriel de `k4MarlinWrapper`
Basée sur https://github.com/key4hep/k4MarlinWrapper.

## Configuring, compiling and installing

```
source /cvmfs/sw.hsf.org/key4hep/setup.sh
```
```
git clone https://github.com/key4hep/k4MarlinWrapper.git
```
```
cd k4MarlinWrapper
```
```
mkdir build install; cd build
```
```
cmake ..
```
```
cmake -DCMAKE_INSTALL_PREFIX=../install ..
```
```
make -j 4
```
```
make install
```

## Running
```
mkdir -p ../test/inputFiles/results
```
Télécharger un fichier d'entré pour le test : https://github.com/AIDASoft/DD4hep/blob/master/DDTest/inputFiles/muons.slcio 
à placer dans le dossier `../test/inputFiles`.
```
k4run ../k4MarlinWrapper/examples/runit.py
```
## Testing and examples
```
### Display available tests
ctest -N
```
### Run all tests
```
ctest
```
### Run specific test with verbose output
```
ctest --verbose -R test_clicReconstruction
```
