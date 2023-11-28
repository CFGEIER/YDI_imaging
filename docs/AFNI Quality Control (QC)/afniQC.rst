=======================
AFNI Quality Control (QC)
=======================

Using afni_proc.py QC measures to assess imaging data & preprocessing 
=======================

afni_proc.py has the following options for Quality Control:

-html_review_style STYLE : specify generation method for HTML review
        e.g.     -html_review_style pythonic
        default: -html_review_style basic

The following instructions assume that the *-html_review_style* pythonic option was used.

First, check to see if Python is installed on your computer by entering the following command:

.. code::

   python -V

Or, if the above fails...

.. code::

   python3 -V

Or, if the "py" command is available, try...

.. code::

   py -V

If your Python version is 3.X (or above), run the following command in the QC directory (typically called 'QC_subj#') generated from afni_proc.py.

.. code::

   python3 -m http.server

If you have Python version 2.X, 

.. code::

   python -m SimpleHTTPServer

..note::

On Windows, try "python -m http.server" or "py -3 -m http.server”


After doing so, your terminal window should indicate that you started a session. 
Next, open up a browser window on your computer and type in the following URL: 

.. code::

localhost:8000

This should make the ".html" files in the QC directory appear as a website. 
