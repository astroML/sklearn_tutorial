
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
       :height: 140
       :target: auto_examples/plot_sdss_filters.html

    .. |banner2| image:: auto_examples/images/plot_sdss_filters_2.png
       :height: 90
       :target: auto_examples/plot_sdss_filters.html

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

    |center-div| |banner1| |banner2| |end-div|

.. only:: html

.. only:: html

 .. sidebar:: Download 
       
    * `PDF, 2 pages per side <./_downloads/nisl.pdf>`_

    * `HTML and example files <https://github.com/nisl/nisl.github.com/zipball/master>`_
    
    * `Source code (github) <https://github.com/nisl/tutorial>`_


.. sectionauthor:: Jake Vanderplas <vanderplas@astro.washington.edu>

.. topic:: Machine Learning for Astronomy with scikit-learn

    ``scikit-learn`` is a Python module integrating classic machine
    learning algorithms in the tightly-knit world of scientific Python
    packages (`numpy <http://numpy.scipy.org>`_, `scipy
    <http://www.scipy.org>`_, `matplotlib
    <http://matplotlib.sourceforge.net/>`_).

    It aims to provide simple and efficient solutions to learning
    problems that are accessible to everybody and reusable in various
    contexts: **machine-learning as a versatile tool for science and
    engineering**.


.. include:: includes/big_toc_css.rst

.. note:: This document is meant to be used with **scikit-learn version
   0.11+** (i.e. the current state of the master branch at the time of
   writing: 2012-03-01).

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

..  
 FIXME: I need the link below to make sure the banner gets copied to the
 target directory.


.. only:: html

 .. raw:: html
 
   <div style='visibility: hidden ; height=0'>

 :download:`nisl.pdf`

 .. raw:: html
 
   </div>

