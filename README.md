# centos_ortools

This guide is for installing ortools on centos.  There are probably better ways to do this.  If so, let me know.

- `wget https://github.com/google/or-tools/releases/download/v5.1/or-tools_python_examples_v5.1.4045.tar.gz`
- `tar xvf or-tools_python_examples_v5.1.4045.tar.gz`
- `cd ortools_examples/`
- `make install`
- `export PYTHONPATH=/home/dxwils3/.local/lib/python2.7/site-packages/`
- `sudo yum install git bison flex python-setuptools python-dev autoconf libtool zlib1g-dev texinfo help2man gawk g++ curl texlive cmake subversion`

Now, when we run `make install`, we find our primary problem.  ortools wants g++ 4.8 (?)

- `yum install devtoolset-2-gcc devtoolset-2-binutils`
- `/opt/rh/devtoolset-2/root/usr/bin/gcc --version`
- `export CC=/opt/rh/devtoolset-2/root/usr/bin/gcc`
- `yum install devtoolset-2-gcc-c++ devtoolset-2-gcc-gfortran`
- `scl enable devtoolset-2 bash`
- `source /opt/rh/devtoolset-2/enable`
- `make all`

This won't build for C# because I didn't bother setting up mono.

- `make test`

The tests should work, but if you fire up `python` at the command line, `import ortools` doesn't work because `make` doesn't install ortools anywhere useful.

So we do this:
- `cp -r ortools $VIRTUALENV_HOME/lib/python2.7/site-packages`

I suppose one could copy it into the system site-packages.  `ortools` is found in the `src` subdirectory in the ortools folder.
