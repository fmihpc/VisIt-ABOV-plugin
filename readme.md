# VisIt Plugin for ABOV (Ascii Brick of Values) files.

Created as a simple interchange format for cartesian 3D data as part of the
[THOR mission](http://thor.irfu.se/) virtual instrument team,

# Installation

You will require a recent version of
[VisIt](https://wci.llnl.gov/simulation/computer-codes/visit/). At the time of
writing, VisIt 2.8 and 2.9 have been tested to work with this plugin.

In the abov plugin folder, you will need to run
```/path/to/visit/bin xml2cmake ABOV.xml```
to create build files.

You can then build the plugin by running
```cmake . && make```

If you get errors about incompatible cmake versions, you can try editing the
version requirement at the top of CmakeLists.txt (although the cleaner way
would be to make sure that your cmake version at least matches the one that
your visit installation was built with).

The plugin will automatically be placed into the current user's VisIt plugin directory.

# File Format

The header format is identical to VisIts own [BOV Format](https://wci.llnl.gov/codes/visit/2.0.0/GettingDataIntoVisIt2.0.0.pdf),
followed by arbitrarily-formated ascii data of the corresponding size. The
ascii data is simply read using `scanf()`, so any whitespace between them is permissible.

Example file:
```
TIME: 153.091282630986996
DATA_SIZE: 3 3 3
DATA_FORMAT: DOUBLE
DATA_COMPONENTS: 1
VARIABLE: example_dataset
BRICK_ORIGIN: -5.0 -5.0 -5.0
BRICK_SIZE: 10. 10. 10.

1 2 3
4 5 6
7 8 9
1e1 1e2 1e3
1e4 1e5 1e6
1e7 1e8 1e9
1e-1 1e-2 1e-3
1e-4 1e-5 1e-6
1e-7 1e-8 1e-9
```
