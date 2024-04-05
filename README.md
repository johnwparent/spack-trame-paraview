# Trame + Paraview

Welcome to the test repo for Trame + Paraview installed
and composed into an environment for easy Trame -> Paraview integration

## Install Instructions

Install Spack! (if you haven't already)
See: <https://spack.readthedocs.io/en/latest/getting_started.html> for more instructions
If you don't want to read an long doc, all you really need to do is have git, and clone
<https://github.com/spack/spack.git> into a directory of your choice.

.. Note: if this note is still here, its likely you'll need to grab a branch off a fork
of Spack as trame is not in the upstream yet. This can be found at https://github.com/johnwparent/spack.git
with the branch named "add-trame-package".
To add run:

`git remote add johnwparent https://github.com/johnwparent/spack.git`

`git fetch johnwparent`

`git checkout -b add-trame-package`


Once that has completed, in your current shell run `share/spack/setup-env.{sh|csh|fish|ps1}`
depending on your preferred shell (if you're using CMD on Windows, `bin\spack_cmd.bat` is what
you're looking for)

This gives you a spack enabled shell and you can now run all Spack commands
(some users find it helpful to add this in their bashrc, but be warned it adds
a non trivial startup oerhead unless modules are disabled)

Now all you need to do is activate the Spack environment vendored with this repo!
(it's the spack yaml file)

with this repo as the current working directory run

`spack env activate .`
This will drop you into a Spack environment, much the same as a Python venv, but for c++ too!

Now all you need to do is install!
`spack install --use-cache`
The `--use-cache` argument will check for existing binaries in the Spack public mirror that match
your request. If no binaries are found, everything will be built from source. This env contains
paraview, so that will take some time.

To speed up builds, you may want to detect a few packages that may be available on your system
like CMake, and any compilers you have available.
`spack compiler find`
`spack external find cmake ninja`

## Test Your Installation

Now we want to test what we just installed. As long as you're in a current Spack env, you should
just be able to proceed as you would as if paraview and trame had been pip installed as normal
**provided you use the Python that Spack installed into your env**
This should be the first python available to you in you PATH
Driving the trame test script found under `./test/RemoteRendering.py` with Spack's Python should
_just work_
