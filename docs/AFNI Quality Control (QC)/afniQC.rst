=======================
AFNI Quality Control (QC)
=======================

Using afni_proc.py QC measures to assess imaging data & preprocessing 
=======================

afni_proc.py has the following options for Quality Control:

-html_review_style STYLE : specify generation method for HTML review
        e.g.     -html_review_style pythonic
        default: -html_review_style basic

The following instructions assume that the -html_review_style pythonic was used. 

First, check to see if Python is installed on your computer by entering the following command:

.. code::

   python -V

or, if the above fails: 

.. code::

   python3 -V
