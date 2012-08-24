Akypuera 
========

Akypuera is a tracing library for MPI applications released under GPLv3.
The library, simplified as aky (linked with `-laky` to MPI apps), uses 
librastro to provide a low memory footprint and low intrusion. The binary
trace files are converted to paje file format using the tool called
`aky_converter`. Akypuera is a word from the tupi language that means trace.

The mpi applications can be linked with libaky this way:

    $ mpicc source_file.c -o mpi_app -laky 
    or
    $ mpicc -c source_file.c
    $ mpicc source_file.o -o mpi_app -laky

You might want to specify the LD_LIBRARY_PATH to contain the path to
`libaky.so`, in order to execute the mpi application. The execution
will create a trace file for each mpi process. A run with 3 processes
generate this list of files:

    rastro-0-0.rst
    rastro-1-0.rst
    rastro-2-0.rst

aky_converter
-------------

Trace files created with akypuera are converted to the [Paje generic
format](http://paje.sf.net) using `aky_converter`, passing as
parameter __all the rst__ files generated by the mpi execution.  The
corresponding paje trace file is printed on __stdout__.

    $ aky_converter rastro*.rst

tau2paje
--------

Converts trace files from the [TAU trace file
format](http://www.cs.uoregon.edu/Research/tau/) to the Paje's generic
file format. [Check the Akypuera's wiki for
__tau2paje__](https://github.com/schnorr/akypuera/wiki/TAUWithAkypuera).

otf22paje
---------

Converts trace files from the [OTF2 trace file
format](http://www.vi-hps.org/projects/score-p/) to Paje's generic
file format.  [Check the Akypuera's wiki for
__otf22paje__](https://github.com/schnorr/akypuera/wiki/OTF2WithAkypuera).
