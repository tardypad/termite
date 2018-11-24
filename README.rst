Termite minimal
===============

This is a stripped down version of the original Termite,
which fits my personal usage.

It adds:

- disabling of client side decorations
- put back the window geometry support
- all digits keys are used for the modify_other_keys config

It removes:

- all features requiring overlays (selection mode, URL hints, scrollbar,...)
- X11 specific code
- feature to launch terminal in directory

It results in a simpler program:

- much shorter code
- no unneeded keybinding
- straightforward packaging

Termite
=======

A keyboard-centric VTE-based terminal, aimed at use within a window manager
with tiling and/or tabbing support.

Termite looks for the configuration file in the following order:
``$XDG_CONFIG_HOME/termite/config``, ``~/.config/termite/config``,
``$XDG_CONFIG_DIRS/termite/config``, ``/etc/xdg/termite/config``.

Termite's exit status is 1 on a failure, including a termination of the child
process from an uncaught signal. Otherwise the exit status is that of the child
process.

BUILDING
========
::

    git clone https://github.com/thestinger/termite.git
    cd termite && make

KEYBINDINGS
===========

+----------------------+---------------------------------------------+
| ``ctrl-shift-r``     | reload configuration file                   |
+----------------------+---------------------------------------------+
| ``ctrl-shift-c``     | copy to CLIPBOARD                           |
+----------------------+---------------------------------------------+
| ``ctrl-shift-v``     | paste from CLIPBOARD                        |
+----------------------+---------------------------------------------+
| ``ctrl-shift-u``     | unicode input (standard GTK binding)        |
+----------------------+---------------------------------------------+
| ``ctrl-shift-e``     | emoji (standard GTK binding)                |
+----------------------+---------------------------------------------+
| ``ctrl-shift-up``    | scroll up a line                            |
+----------------------+---------------------------------------------+
| ``ctrl-shift-down``  | scroll down a line                          |
+----------------------+---------------------------------------------+
| ``shift-pageup``     | scroll up a page                            |
+----------------------+---------------------------------------------+
| ``shift-pagedown``   | scroll down a page                          |
+----------------------+---------------------------------------------+
| ``ctrl-shift-l``     | reset and clear                             |
+----------------------+---------------------------------------------+
| ``ctrl-+``           | increase font size                          |
+----------------------+---------------------------------------------+
| ``ctrl--``           | decrease font size                          |
+----------------------+---------------------------------------------+
| ``ctrl-=``           | reset font size to default                  |
+----------------------+---------------------------------------------+

PADDING
=======

Internal padding can be added by using CSS to style Termite. Adding
the following snippet to ``$XDG_CONFIG_HOME/gtk-3.0/gtk.css`` (or
``~/.config/gtk-3.0/gtk.css``) will add uniform 2px padding around the edges:

.. code:: css

    .termite {
        padding: 2px;
    }

This can also be used to add varying amounts of padding to each side via
standard usage of the CSS padding property.

TERMINFO
========

When working on a remote system with termite's terminfo missing, an error might
occur:

::

    Error opening terminal: xterm-termite

To solve this issue, install the termite terminfo on your remote system.

On Arch Linux:

::

        pacman -S termite-terminfo

On other systems:


::

    wget https://raw.githubusercontent.com/thestinger/termite/master/termite.terminfo
    tic -x termite.terminfo
