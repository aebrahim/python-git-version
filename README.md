python-git-version
==================

Generate [pep440](http://legacy.python.org/dev/peps/pep-0440/) compliant
version strings from git for python projects

This will read the version from ```git desribe``` (assuming it is pep440
compliant already) and generate a descriptive version string. For example, if
the latest tag is 0.1b1 and 3 commits have been made since,
```0.1b1.post3+gitabcdef0``` will be the resulting version string. For release
versions uploaded to the [package index](https://pypi.python.org/pypi), the
githash should be left off as per pep 440, which can be done by passing
```pep400=True``` to ```get_version```.

To get versions when not in a git repository, a file called ```VERSION```
should be created in the same folder containing the same version as the git
tag. This can either be updated manually on each release by editing the file,
or the file can be generated automatically when creating packages for
distribtuion (for example when running sdist). It is important to ensure this
file is also installed along with the package.

Directions
----------

1. Copy ```version.py``` into your project. It's in the public domain.
2. In your package (for example in the ```__init__.py``` file), add
   ```__version__ = get_version(pep440=False)```
3. In the ```setup()``` function of ```setup.py```, pass in
   ```version=get_version(pep440=True)``` as a keyword argument.
4. Create the ```VERSION``` file with the appropriate version string, or setup
   any automatic file writing you desire. Ensure that ```VERSION``` is
   included with your installation.
5. Create a git tag.
