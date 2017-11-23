# Atomix helloword app

## to install ##

Clone axhello

Check that the path variable ATOMIX_INSTALL_DIR is set. If not, add to .bashrc:

export ATOMIX_INSTALL_DIR=$ATOMIX_ROOT/build

Set up the path to dsplib by export DSPLIB_ROOT variable in bashrc. This is available in tiextlibs installed as part of atomix setup:

export DSPLIB_ROOT=$TIEXTLIBS_ROOT/dsplib_c66x_3_2_0_1


## to build ##

```
$ cd axhello

$ autoreconf --install

$ mkdir build

$ cd build

$ ../_configure  #add debug=4 to the command to see prints during run

$ make  #ignore link errors and make again
$ make  #this one links without errors
```

