Build PDF format for non-ASCII languages
========================================

Sphinx comes with support for different `LaTeX engines`_ that support non-ASCII languages,
like Japanese or Chinese, for example.
By default Sphinx uses ``pdflatex``,
which does not have good support for Unicode characters and may make the PDF builder to fail on these languages.

.. _LaTeX engines: http://www.sphinx-doc.org/en/master/usage/configuration.html#confval-latex_engine

In case you want to build your documentation in PDF format you need to configure Sphinx properly,
so Read the Docs can execute the proper commands depending on these settings.
There are `several settings that can be defined`_ (all the ones starting with ``latex_``),
to modify Sphinx and Read the Docs behavior to make your documentation to build properly.

.. _several settings that can be defined: http://www.sphinx-doc.org/en/master/usage/configuration.html#options-for-latex-output

Here is an useful example of the settings defined in ``conf.py`` for many Chinese projects:

.. code-block:: python

    latex_engine = 'xelatex'
    latex_use_xindy = False
    latex_elements = {
        'preamble': '\\usepackage[UTF8]{ctex}\n',
    }


.. note::

   ``xindy`` is currently not supported by Read the Docs,
   but we plan to support it in the near future.
