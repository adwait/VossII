Voss II
=======

Voss II is a software suite for describing and reasoning about circuits.
Circuits, and properties about them, are described in a functional language
called *fl*.

Fl is a statically typed language with call-by-need semantics (also known as
*lazy evaluation*) and binary decision diagrams built right into the language
itself.

Voss II has been tested and found to work on Debian, Ubuntu, Fedora, Red Hat
and OpenSUSE. If you're using it on another distribution, we'd love to hear
from you!


Introduction to VossII
----------------------
There is a 
["Getting Started with VossII and fl"](https://teamvoss.github.io/tutorial)
tutorial in the doc/fl_tutorial directory (you can do firefox doc/fl_tutorial/fl_tutorial.html or your choice of browser to see it)

There is also a more extensive 
[User's Guide](https://github.com/TeamVoss/VossII/blob/master/doc/fl_guide.pdf)



Installation
------------

Download our
[pre-built binaries](https://github.com/TeamVoss/VossII/releases/latest)
and unpack them to your directory of choice, then put <installation-directory>/bin in your search path and you will be able to run the fl interpreter by simply invokng fl. Note that you need the <voss dir>/bin in your search path for the Verilog reader to work, and it must be earlier than any paths containing other versions of yosys!


Voss II depends on Tk for its graphical bits. If the fl interpreter dies with
an angry message about not being able to find `wish`, you need to install it:

* **On Ubuntu/other Debian-based**
  ```shell
  sudo apt install tk
  ```
* **On Fedora/Red Hat**
  ```shell
  sudo yum install tk
  ```
* **On SUSE**
  ```shell
  sudo zypper install tk
  ```

Building (on Ubuntu/Debian)
---------------------------

If you want to build your own libraries you will first need to install some
build dependencies:

```shell
sudo apt-get install gcc g++ doxygen flex bison gawk \
                     libz-dev tcl-dev tk-dev libc6-dev \
                     clang libreadline-dev python3 imagemagick pandoc
```

Then, from the root of the VossII repository (assuming you've already
cloned it), run:

```shell
make -C src install
```

This will build Voss II and install it _into the repository root directory_.
If you want to build a distributable binary package, you should install run:

```shell
make -C src clean_package
```

This will create a file `voss.tar.bz2` in the repository root directory.

Finally, if you just want to build a Voss II package in a pristine environment,
without having to sully your system with a bunch of dependencies, you can use
Docker to build `voss.tar.bz2` instead:

```shell
make -C src docker_package
```

If you're not a member of the `docker` group on your system, you will need to
run the above command as root.

To verify the installation, run:


```shell
fl
```

