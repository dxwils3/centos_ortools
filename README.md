# centos_ortools

I just want to record the steps to get this done.

First, follow the instructions on the google page: https://developers.google.com/optimization/introduction/installing.html#unix_source.

Now, when we run `make install`, we find our primary problem.  ortools wants a version of g++ that isn't on centos.

Follow the instructions on this page to fix that: https://gist.github.com/giwa/b1fb1e44dc0a7d270881

Now, we can do `make all` back in the ortools directory.

This won't build for C# because I didn't bother setting up mono.

- `make test`

The tests should work, but if you fire up `python` at the command line, `import ortools` doesn't work because `make` doesn't install ortools anywhere useful.

The final step is to
`export PYTHONPATH=$PYTHONPATH:or-tools-path`

where or-tools-path points to the `src` directory in the or-tools directory, wherever you put it.

It should work now.
