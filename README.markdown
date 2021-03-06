substratestack
==============

Introduction
------------

*substratestack* is a Python module that helps simplifying substrate stackups
for use in *Momentum* and *Sonnet*. It was initially written for use in an MMIC
design methodology, but it might also be useful for PCB design.

The design of MMIC passives such as planar inductors and transmission lines
requires simulations using electromagnetic solvers, for instance *ADS Momentum*
or *Sonnet em*. These require an accurate definition of the substrate stack in
order to output correct models. The user typically copies the substrate stack
definition from the documentation provided by the IC foundry into the solver by
means of its GUI. Often the stack needs to be simplified to keep simulation
times down. The simplification and manual entry of the stack is a tedious and
error-prone process. *substratestack* tries to make this process quicker and
less error-prone.

*substratestack* takes the detailed definition of a substrate stackup describing
the oxide layers and metals of an IC or PCB technology. Optionally, metals can
be removed from the stack to reduce simulation times. *substratestack* can then
merge oxide layers, automatically taking care of calculating the equivalent
permittivity. It can also write out a visualization of the stack, before and
after oxide merging, so the correctness can be verified.

Finally, the simplified stack definition can be exported to a *Momentum* `slm`
file or a Sonnet project for direct inclusion in these solvers.


Installation
------------

The *substratestack* package requires at least version 2.4 of Python. Python 3.x
is not supported at the moment. In addition, the [ReportLab Toolkit][reportlab]
is required for rendering the stacks to PDF. On Windows, you should install
ReportLab using the provided [Windows installers][rl-download].

The most convenient option for getting *substratestack* is by using [pip][pip]
or [easy_install][setuptools]. To automatically download the archive from
[PyPI][pypi] install it, run

    pip install substratestack
    
or

    easy_install substratestack

If you have instead downloaded the source package, you can install it by
unpacking the archive and running

    python setup.py install


[reportlab]: http://www.reportlab.com/software/opensource/rl-toolkit/
[rl-download]: http://www.reportlab.com/software/opensource/rl-toolkit/download/
[pip]: http://pip.openplans.org/
[setuptools]: http://pypi.python.org/pypi/setuptools
[pypi]: http://pypi.python.org


Usage
-----

**Disclaimer: While *substratestack* has been successfully used in MMIC-design
by the author, there is no guarantuee that it is bug-free. Be sure to double and
triple-check its output.**

A documented example is included in the `examples` directory. `example.py`
contains the substrate definition of a hypothetical six-metal-layer CMOS
process. Run `example.py` to have *substratestack* render the stack to PDF:

    python example.py

`example_ME5ME6.py` imports the stack from `example.py` and removes all metal
layers but the top two. It simplifies the resulting stack and writes substrate
definition files in the *Momentum* and *Sonnet* formats. Run `example_ME5ME6.py`
to generate the PDFs and substrate definition files:

    python example_ME5ME6.py

Refer to the `example.py` and `example_ME5ME6.py` for specific documentation on
how to define, simplify and render substrate stacks. The [wiki][wiki] offers
sample PDFs generated by `example.py` and `example_ME5ME6.py`.


[wiki]: http://github.com/bmachiel/python-substratestack/wiki
