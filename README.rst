.. |build| image:: http://build.cloudef.pw/build/orbment/master/linux%20x86_64/current/status.svg
.. _build: http://build.cloudef.pw/build/orbment/master/linux%20x86_64

.. image:: http://cloudef.pw/armpit/loliwm-gh.png
:IRC: #orbment @ freenode
:Video: https://www.youtube.com/watch?v=nh_7aqNtrik
:Build: |build|_

Orbment is modular compositor for Wayland with flexible plugin architecture where plugins may co-operate with each other.
The core consist of small code base which provide plugin management, and hooks api for plugins.
Core plugins are used to provide functionality you would expect from bare bones tiling window manager.

THIS IS A FORK OF cloudef/orbment USING joe9/wlc and skb TO SUPPORT STICKY KEYS

OPTIONS
-------

Basic information about what you can currently do in ``orbment``.

+-----------------------+------------------------------------------------+
| ``--log FILE``        | Logs output to specified ``FILE``.             |
+-----------------------+------------------------------------------------+

See `wlc documentation <https://github.com/Cloudef/wlc>`_ for ``wlc`` specific options.

KEYBINDS
--------

Note that these keybinds are temporary until configuration is added.

+-----------------+------------------------------------------------------+
| ``mod-return``  | Opens a terminal emulator.                           |
+-----------------+------------------------------------------------------+
| ``mod-p``       | Opens ``bemenu-run``.                                |
+-----------------+------------------------------------------------------+
| ``mod-w``       | Rotates through available layouts.                   |
+-----------------+------------------------------------------------------+
| ``mod-l``       | Rotates focus through outputs.                       |
+-----------------+------------------------------------------------------+
| ``mod-j, k``    | Rotates focus through clients.                       |
+-----------------+------------------------------------------------------+
| ``mod-f``       | Toggles fullscreen.                                  |
+-----------------+------------------------------------------------------+
| ``mod-[1..n]``  | Activate space.                                      |
+-----------------+------------------------------------------------------+
| ``mod-F1..F10`` | Moves focused client to corresponding space.         |
+-----------------+------------------------------------------------------+
| ``mod-z, x, c`` | Moves focused client to output 1, 2 and 3            |
|                 | respectively.                                        |
+-----------------+------------------------------------------------------+
| ``mod-h``       | Cycles clients.                                      |
+-----------------+------------------------------------------------------+
| ``mod-q``       | Closes focused client.                               |
+-----------------+------------------------------------------------------+
| ``mod-i, o``    | Shifts the cut of the nmaster layout to shrink or    |
|                 | expand the view.                                     |
+-----------------+------------------------------------------------------+
| ``mod-s``       | Takes a screenshot in PNG format.                    |
+-----------------+------------------------------------------------------+
| ``mod-esc``     | Quits ``orbment``.                                   |
+-----------------+------------------------------------------------------+

KEYBOARD LAYOUT
---------------

You can set your preferred keyboard layout using ``XKB_DEFAULT_LAYOUT``.

.. code:: sh

    XKB_DEFAULT_LAYOUT=gb orbment

RUNNING ON TTY
--------------

If you have ``logind``, you can just run ``orbment`` normally.

Without ``logind`` you need to suid the orbment binary to root user.
The permissions will be dropped runtime.

BUILDING
--------

See `wlc documentation <https://github.com/Cloudef/wlc>`_ for dependencies.

You can build bootstrapped version of ``orbment`` which also includes ``wlc`` with the following steps.

.. code:: sh

    git submodule update --init --recursive              # - initialize and fetch submodules
    mkdir target && cd target                            # - create build target directory
    cmake -DCMAKE_BUILD_TYPE=Upstream -DSOURCE_WLC=ON .. # - run CMake
    make                                                 # - compile

    # You can now run
    ./src/orbment

If built in Debug mode, ``./plugins`` is added to plugin search paths, and you can run ``orbment`` straight
from the build directory and it will find the core plugins. This is useful for testing development version,
bootstrapping or developing plugins.

PACKAGING
---------

For now you can look at the `AUR recipe <https://aur.archlinux.org/packages/orbment-git/>`_  for a example.

CONTRIBUTING
------------

See the `CONTRIBUTING <CONTRIBUTING.rst>`_ for more information.

SIMILAR SOFTWARE
----------------

- `Velox <https://github.com/michaelforney/velox>`_ - Tiling wayland compositor based on swc
- `Waysome <https://github.com/waysome/waysome>`_ - Scriptable wayland compositor
- `sway <https://github.com/SirCmpwn/sway>`_ - i3-compatible window manager for Wayland
