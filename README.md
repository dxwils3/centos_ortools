# centos_ortools

This guide is for installing ortools on centos.  There are probably better ways to do this.

First, follow the instructions on the google page: https://developers.google.com/optimization/introduction/installing.html#unix_source.

Now, when we run `make install`, we find our primary problem.  ortools wants a version of g++ that isn't on centos.

Follow the instructions on this page to fix that: https://gist.github.com/giwa/b1fb1e44dc0a7d270881

Now, we can do `make all` back in the ortools directory.

This won't build for C# because I didn't bother setting up mono.

- `make test`

The tests should work, but if you fire up `python` at the command line, `import ortools` doesn't work because `make` doesn't install ortools anywhere useful.


I suppose one could copy it into the system site-packages.  `ortools` is found in the `src` subdirectory in the ortools folder.
