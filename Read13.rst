# Matplotlib
## Introduction
matplotlib is probably the single most used Python package for 2D-graphics.
It provides both a very quick way to visualize data from Python and publication-quality figures in many formats.

### IPython
IPython is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs,
access to shell commands, improved debugging and much more. It allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.

### pyplot
pyplot provides a convenient interface to the matplotlib object-oriented plotting library.
It is modeled closely after Matlab(TM). Therefore, the majority of plotting commands in pyplot have Matlab(TM) analogs with similar arguments.
Important commands are explained with interactive examples.


Figures
-------

A figure is the windows in the GUI that has "Figure #" as title. Figures
are numbered starting from 1 as opposed to the normal Python way starting
from 0. This is clearly MATLAB-style.  There are several parameters that
determine what the figure looks like:

==============  ======================= ============================================
Argument        Default                 Description
==============  ======================= ============================================
num             1                       number of figure
figsize         figure.figsize          figure size in in inches (width, height)
dpi             figure.dpi              resolution in dots per inch
facecolor       figure.facecolor        color of the drawing background
edgecolor       figure.edgecolor        color of edge around the drawing background
frameon         True                    draw figure frame or not
==============  ======================= ============================================

The defaults can be specified in the resource file and will be used most of the
time. Only the number of the figure is frequently changed.

When you work with the GUI you can close a figure by clicking on the x in the
upper right corner. You can also close a figure programmatically by calling
close. Depending on the argument it closes (1) the current figure (no
argument), (2) a specific figure (figure number or figure instance as
argument), or (3) all figures (all as argument).

As with other objects, you can set figure properties with the set_something methods.


Subplots
--------

With subplot you can arrange plots in a regular grid. You need to specify the
number of rows and columns and the number of the plot. Note that the `gridspec
<http://matplotlib.sourceforge.net/users/gridspec.html>`_ command is a more
powerful alternative.

.. image:: figures/subplot-horizontal.png
   :target: scripts/subplot-horizontal.py
.. image:: figures/subplot-vertical.png
   :target: scripts/subplot-vertical.py
.. image:: figures/subplot-grid.png
   :target: scripts/subplot-grid.py
.. image:: figures/gridspec.png
   :target: scripts/gridspec.py



Axes
----

Axes are very similar to subplots but allow placement of plots at any location
in the figure. So if we want to put a smaller plot inside a bigger one we do
so with axes.

.. image:: figures/axes.png
   :target: scripts/axes.py
.. image:: figures/axes-2.png
   :target: scripts/axes-2.py


Ticks
-----

Well formatted ticks are an important part of publishing-ready
figures. Matplotlib provides a totally configurable system for ticks. There are
tick locators to specify where ticks should appear and tick formatters to give
ticks the appearance you want. Major and minor ticks can be located and
formatted independently from each other. By default minor ticks are not shown,
i.e. there is only an empty list for them because it is as NullLocator (see
below).

Tick Locators
.............

There are several locators for different kind of requirements:


.. list-table::
   :widths: 20 70
   :header-rows: 1

   * - Class
     - Description


   * - ``NullLocator``
     - No ticks.

       .. image:: figures/ticks-NullLocator.png
     
   * - ``IndexLocator``
     - Place a tick on every multiple of some base number of points plotted.

       .. image:: figures/ticks-IndexLocator.png

   * - ``FixedLocator``
     - Tick locations are fixed.

       .. image:: figures/ticks-FixedLocator.png

   * - ``LinearLocator``
     - Determine the tick locations.

       .. image:: figures/ticks-LinearLocator.png

   * - ``MultipleLocator``
     - Set a tick on every integer that is multiple of some base.

       .. image:: figures/ticks-MultipleLocator.png

   * - ``AutoLocator``
     - Select no more than n intervals at nice locations.

       .. image:: figures/ticks-AutoLocator.png

   * - ``LogLocator``
     - Determine the tick locations for log axes.

       .. image:: figures/ticks-LogLocator.png

All of these locators derive from the base class matplotlib.ticker.Locator.
You can make your own locator deriving from it. Handling dates as ticks can be
especially tricky. Therefore, matplotlib provides special locators in
matplotlib.dates.


Animation
=========

For quite a long time, animation in matplotlib was not an easy task and was
done mainly through clever hacks. However, things have started to change since
version 1.1 and the introduction of tools for creating animation very
intuitively, with the possibility to save them in all kind of formats (but don't
expect to be able to run very complex animations at 60 fps though).

.. admonition:: Documentation

   *  See `Animation <http://matplotlib.org/api/animation_api.html>`_

The most easy way to make an animation in matplotlib is to declare a
FuncAnimation object that specifies to matplotlib what is the figure to
update, what is the update function and what is the delay between frames.


Drip drop
---------

A very simple rain effect can be obtained by having small growing rings
randomly positioned over a figure. Of course, they won't grow forever since the
wave is supposed to damp with time. To simulate that, we can use a more and
more transparent color as the ring is growing, up to the point where it is no
more visible. At this point, we remove the ring and create a new one.

First step is to create a blank figure:

.. code:: python

   # New figure with white background
   fig = plt.figure(figsize=(6,6), facecolor='white')

   # New axis over the whole figure, no frame and a 1:1 aspect ratio
   ax = fig.add_axes([0,0,1,1], frameon=False, aspect=1)
