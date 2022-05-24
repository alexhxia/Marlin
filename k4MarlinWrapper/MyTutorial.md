# Mon tutoriel de `k4MarlinWrapper`
Basée sur https://github.com/key4hep/k4MarlinWrapper.

## Configuring, compiling and installing

```
$ source /cvmfs/sw.hsf.org/key4hep/setup.sh
Setting up the latest Key4HEP software stack from CVMFS ...
 ...  Key4HEP release: key4hep-stack/2022-05-21
 ... Use the following command to reproduce the current environment: 
 ... 
         source /cvmfs/sw.hsf.org/spackages5/key4hep-stack/2022-05-21/x86_64-centos7-gcc11.2.0-opt/7c3ak/setup.sh
 ... 
 ... done. 
```
```
source /cvmfs/sw.hsf.org/spackages5/key4hep-stack/2022-05-21/x86_64-centos7-gcc11.2.0-opt/7c3ak/setup.sh
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
mkdir -p ../test/inputFiles ../../results
```
Télécharger un fichier d'entré pour le test : https://github.com/AIDASoft/DD4hep/blob/master/DDTest/inputFiles/muons.slcio 
à placer dans le dossier `../test/inputFiles`.
```
k4run ../k4MarlinWrapper/examples/runit.py 1> ../../results/k4run.out 2> ../../results/k4run.err
```
## Testing and examples

### Display available tests
```
ctest -N
```
```
$ ctest -N
Test project /path/to/build
  Test #1: simple_processors
  Test #2: simple_processors2
  Test #3: clicRec
  Test #4: converter_constants
  Test #5: edm_converters
  Test #6: all_events_bounds
  Test #7: over_total_events
  Test #8: same_num_io
  Test #9: clicRec_lcio_mt

Total Tests: 9

```
### Run all tests
```
ctest
```
### Run specific test with verbose output
```
ctest --verbose -R test_clicReconstruction
```
