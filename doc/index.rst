
..
    We are putting the title as a raw HTML so that it doesn't appear in
    the contents
    
.. raw:: html

    <h1>Machine Learning for Astronomical Data Analysis</h1>
    <style type="text/css">
    p {
        margin: 7px 0 7px 0 ;
    }
    span.linkdescr a {
        color:  #3E4349 ;
    }
    div.banner img {
        vertical-align: middle;
    }
    </style>

..  
   Here we are building a banner: a javascript selects randomly 4 images in 
   the list

.. only:: html

    .. |banner1| image:: auto_examples/images/plot_sdss_filters_1.png
       :height: 120
       :target: auto_examples/plot_sdss_filters.html

    .. |banner2| image:: auto_examples/images/plot_sdss_filters_2.png
       :height: 120
       :target: auto_examples/plot_sdss_filters.html

    .. |banner3| image:: auto_examples/images/plot_sdss_images_1.png
       :height: 90
       :target: auto_examples/plot_sdss_images.html

    .. |banner4| image:: auto_examples/images/plot_ML_flow_chart_1.png
       :height: 120
       :target: auto_examples/plot_ML_flow_chart.html

    .. |banner5| image:: auto_examples/images/plot_sdss_photoz_1.png
       :height: 120
       :target: auto_examples/plot_sdss_photoz.html

    .. |banner6| image:: auto_examples/images/plot_sdss_specPCA_1.png
       :height: 120
       :target: auto_examples/plot_sdss_specPCA.html

    .. |center-div| raw:: html

        <div style="text-align: center; vertical-align: middle; margin: -7px 0 -10px 0;" id="banner" class="banner">

    .. |end-div| raw:: html

        </div>

        <SCRIPT>
        // Function to select 4 imgs in random order from a div
        function shuffle(e) {       // pass the divs to the function
          var replace = $('<div>');
          var size = 4;
          var num_choices = e.size();

          while (size >= 1 && num_choices >= 1) {
            var rand = Math.floor(Math.random() * num_choices);
            var temp = e.get(rand);      // grab a random div from our set
            replace.append(temp);        // add the selected div to our new set
            e = e.not(temp); // remove our selected div from the main set
            size--;
            num_choices--;
          }
          $('#banner').html(replace.html() ); // update our container div 
                                              // with the new, randomized divs
        }
        shuffle ($('#banner a.external'));
        </SCRIPT>

    |center-div| |banner1| |banner2| |banner3| |banner4| |banner5| |banner6| |end-div|

.. only:: html

.. only:: html

 .. sidebar:: Download 
    
    * `Source code (github) <https://github.com/astroML/sklearn_tutorial>`_

    * :download:`PDF of tutorial <sklearn_tutorial.pdf>`
        
    * :download:`tarball of exercises <exercises.tgz>`


.. sectionauthor:: Jake Vanderplas <vanderplas@astro.washington.edu>

.. topic:: Machine Learning for Astronomy with scikit-learn

   This tutorial offers a brief introduction to the fields of machine
   learning and statistical data analysis, and their application to
   several problems in the field of astronomy.  These learning tasks
   are enabled by the tools available in the open-source package
   `scikit-learn`_.

   `scikit-learn`_ is a Python module integrating classic machine
   learning algorithms in the tightly-knit world of scientific Python
   packages (`numpy`_, `scipy`_, `matplotlib`_).  It aims to provide
   simple and efficient solutions to learning problems that are accessible
   to everybody and reusable in various contexts:
   **machine-learning as a versatile tool for science and engineering**.

   Many of the examples and exercises in this tutorial require the
   `ipython notebook`_, a tool which provides an intuitive web-based
   interactive environment for scientific python.  Some of the material
   in the notebooks is duplicated in the following pages, but ipython
   notebook is required for some parts. For information on how to download
   the associated notebooks, see the :ref:`sklearn_tutorial_setup` page.

.. _`scikit-learn`: http://www.scikit-learn.org
.. _`numpy`: http://numpy.scipy.org
.. _`scipy`: http://www.scipy.org
.. _`matplotlib`: http://matplotlib.sourceforge.net
.. _`ipython notebook`: http://ipython.org/ipython-doc/stable/interactive/htmlnotebook.html

.. include:: includes/big_toc_css.rst

.. note:: This document is meant to be used with **scikit-learn version
   0.11+**.  Find the latest version `here <scikit-learn>`_.

.. toctree::
   :numbered:
   :maxdepth: 2

   setup
   general_concepts
   practical
   classification
   regression
   dimensionality_reduction
   exercises
   auto_examples/index

.. toctree::
   :hidden:

   AUTHORS

..  
 FIXME: I need the link below to make sure the banner gets copied to the
 target directory.


.. only:: html

 .. raw:: html
 
   <div style='visibility: hidden ; height=0'>

 .. raw:: html
 
   </div>

