# Python Prompt Toolkit

|Build Status| |AppVeyor| |PyPI| |RTD| |License| |Codecov|

.. image :: https://github.com/prompt-toolkit/python-prompt-toolkit/raw/master/docs/images/logo_ @abstr_number px.png

`prompt_toolkit` _is a library for building powerful interactive command line applications in Python._

Read the `documentation on readthedocs <http://python-prompt-toolkit.readthedocs.io/en/stable/>`_.

NOTICE: prompt_toolkit @abstr_number . @abstr_number 

* * *

Please notice that this branch is the `prompt_toolkit` _* @abstr_number . @abstr_number *_ branch. For most users, it should be compatible with `prompt_toolkit` _* @abstr_number . @abstr_number *_ , but it requires at least _*Python @abstr_number . @abstr_number *_. On the plus side, `prompt_toolkit` _* @abstr_number . @abstr_number *_ is completly type annotated and uses asyncio natively.

Gallery

* * *

`ptpython <http://github.com/prompt-toolkit/ptpython/>`_ is an interactive Python Shell, build on top of `prompt_toolkit`.

.. image :: https://github.com/prompt-toolkit/python-prompt-toolkit/raw/master/docs/images/ptpython.png

`More examples <https://python-prompt-toolkit.readthedocs.io/en/stable/pages/gallery.html>`_ ^^^^

prompt_toolkit features

* * *

`prompt_toolkit` could be a replacement for `GNU readline <https://tiswww.case.edu/php/chet/readline/rltop.html>`_, but it can be much more than that.

Some features:

  * **Pure Python**.
  * Syntax highlighting of the input while typing. (For instance, with a Pygments lexer.)
  * Multi-line input editing.
  * Advanced code completion.
  * Both Emacs and Vi key bindings. (Similar to readline.)
  * Even some advanced Vi functionality, like named registers and digraphs.
  * Reverse and forward incremental search.
  * Works well with Unicode double width characters. (Chinese input.)
  * Selecting text for copy/paste. (Both Emacs and Vi style.)
  * Support for `bracketed paste <https://cirw.in/blog/bracketed-paste>`_.
  * Mouse support for cursor positioning and scrolling.
  * Auto suggestions. (Like `fish shell <http://fishshell.com/>`_.)
  * Multiple input buffers.
  * No global state.
  * Lightweight, the only dependencies are Pygments, six and wcwidth.
  * Runs on Linux, OS X, FreeBSD, OpenBSD and Windows systems.
  * And much more...



Feel free to create tickets for bugs and feature requests, and create pull requests if you have nice patches that you would like to share with others.

Installation

* * *

::
    
    
    pip install prompt_toolkit
    

For Conda, do:

::
    
    
    conda install -c https://conda.anaconda.org/conda-forge prompt_toolkit
    

About Windows support

* * *

`prompt_toolkit` is cross platform, and everything that you build on top should run fine on both Unix and Windows systems. Windows support is best on recent Windows @abstr_number builds, for which the command line window supports vt @abstr_number escape sequences. (If not supported, we fall back to using Win @abstr_number APIs for color and cursor movements).

It's worth noting that the implementation is a "best effort of what is possible". Both Unix and Windows terminals have their limitations. But in general, the Unix experience will still be a little better.

For Windows, it's recommended to use either `cmder <http://cmder.net/>`_ or `conemu <https://conemu.github.io/>`_.

Getting started

* * *

The most simple example of the library would look like this:

.. code:: python
    
    
    from prompt_toolkit import prompt
    
    if __name__ == '__main__':
        answer = prompt('Give me some input: ')
        print('You said: %s' % answer)
    

For more complex examples, have a look in the `examples` directory. All examples are chosen to demonstrate only one thing. Also, don't be afraid to look at the source code. The implementation of the `prompt` function could be a good start.

Note for Python @abstr_number : all strings are expected to be unicode strings. So, either put a small `u` in front of every string or put `from __future__ import unicode_literals` at the start of the above example.

Philosophy

* * *

The source code of `prompt_toolkit` should be **readable** , **concise** and **efficient**. We prefer short functions focusing each on one task and for which the input and output types are clearly specified. We mostly prefer composition over inheritance, because inheritance can result in too much functionality in the same object. We prefer immutable objects where possible (objects don't change after initialization). Reusability is important. We absolutely refrain from having a changing global state, it should be possible to have multiple independent instances of the same code in the same process. The architecture should be layered: the lower levels operate on primitive operations and data structures giving -- when correctly combined -- all the possible flexibility; while at the higher level, there should be a simpler API, ready-to-use and sufficient for most use cases. Thinking about algorithms and efficiency is important, but avoid premature optimization.

`Projects using prompt_toolkit <PROJECTS.rst>`_

* * *

Special thanks to

* * *

  * `Pygments <http://pygments.org/>`_: Syntax highlighter.
  * `wcwidth <https://github.com/jquast/wcwidth>`_: Determine columns needed for a wide characters.



.. |Build Status| image:: https://api.travis-ci.org/prompt-toolkit/python-prompt-toolkit.svg?branch=master :target: https://travis-ci.org/prompt-toolkit/python-prompt-toolkit#

.. |PyPI| image:: https://img.shields.io/pypi/v/prompt_toolkit.svg :target: https://pypi.python.org/pypi/prompt-toolkit/ :alt: Latest Version

.. |AppVeyor| image:: https://ci.appveyor.com/api/projects/status/ @abstr_number r @abstr_number s @abstr_number skrgm @abstr_number ubva?svg=true :target: https://ci.appveyor.com/project/prompt-toolkit/python-prompt-toolkit/

.. |RTD| image:: https://readthedocs.org/projects/python-prompt-toolkit/badge/ :target: https://python-prompt-toolkit.readthedocs.io/en/master/

.. |License| image:: https://img.shields.io/github/license/prompt-toolkit/python-prompt-toolkit.svg :target: https://github.com/prompt-toolkit/python-prompt-toolkit/blob/master/LICENSE

.. |Codecov| image:: https://codecov.io/gh/prompt-toolkit/python-prompt-toolkit/branch/master/graphs/badge.svg?style=flat :target: https://codecov.io/gh/prompt-toolkit/python-prompt-toolkit/