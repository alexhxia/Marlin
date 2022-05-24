# Mon tutoriel de `k4MarlinWrapper`
Basée sur https://github.com/key4hep/k4MarlinWrapper.

## Configuring, compiling and installing

```
$ source /cvmfs/sw-nightlies.hsf.org/key4hep/setup.sh
Setting up the latest Key4HEP software stack from CVMFS ...
 ...  Key4HEP release: key4hep-stack/master-2022-05-24
 ... Use the following command to reproduce the current environment: 
 ... 
         source /cvmfs/sw-nightlies.hsf.org/spackages5/key4hep-stack/master-2022-05-24/x86_64-centos7-gcc11.2.0-opt/ikkhy/setup.sh
 ... 
 ... done. 

```
```
source /cvmfs/sw-nightlies.hsf.org/spackages5/key4hep-stack/master-2022-05-24/x86_64-centos7-gcc11.2.0-opt/ikkhy/setup.sh
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
```
$ ctest
Test project /home/ilc/ahocine/k4MarlinWrapper/build
    Start 1: simple_processors
1/9 Test #1: simple_processors ................   Passed    4.34 sec
    Start 2: simple_processors2
2/9 Test #2: simple_processors2 ...............   Passed    4.72 sec
    Start 3: clicRec
3/9 Test #3: clicRec ..........................   Passed   82.07 sec
    Start 4: converter_constants
4/9 Test #4: converter_constants ..............   Passed    5.36 sec
    Start 5: edm_converters
5/9 Test #5: edm_converters ...................   Passed    1.56 sec
    Start 6: all_events_bounds
6/9 Test #6: all_events_bounds ................   Passed    4.34 sec
    Start 7: over_total_events
7/9 Test #7: over_total_events ................   Passed    4.31 sec
    Start 8: same_num_io
8/9 Test #8: same_num_io ......................   Passed    2.64 sec
    Start 9: clicRec_lcio_mt
9/9 Test #9: clicRec_lcio_mt ..................   Passed   86.75 sec

100% tests passed, 0 tests failed out of 9

Total Test time (real) = 196.13 sec
```

### Run specific test with verbose output
```
ctest --verbose -R test_clicReconstruction
```
