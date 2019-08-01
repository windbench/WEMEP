WEMEP: Wind Energy Model Evaluation Protocol
============================================

Purpose
-------

This site hosts open-source documentation for a Wind Energy Model Evaluation Protocol. The purpose is to provide guidance on how to perform formal verification, validation and uncertainty quantification of models used by wind energy applications. 

The protocol is defined in generic model-agnostic terms so it can be adopted by any modeling community. Then, each community can document their interpretation of the protocol in the definition of suitable validation strategies for the intended uses of their models. Ultimately, this results in the definition of a hierarchy of verification and validation cases of increasing complexity. These cases are curated by the community through model intercomparison benchmarks archived as public data repositories.     

The protocol is launched from the IEA-Wind Task 31 “Wakebench_” which is focused on the evaluation of wind farm flow models. This includes models for the atmospheric boundary layer, to simulate wind conditions for wind resource and site suitability assessment, as well as wake models for the assessment of wind farm array efficiency and loads in connection to wind farm design.

Other research communities are welcomed to integrate their model evaluation strategies and benchmarks. 

.. _Wakebench: https://community.ieawind.org/task31/home

How to Contribute
-----------------
The documentation is written using Sphinx_ docs based on reStructuredText_. Then, it is automatically built into a `Read The Docs`_ website. You can find information about how to contribute at the `Community Guide`_.  

.. _Sphinx: http://www.sphinx-doc.org/
.. _reStructuredText: http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html
.. _Read The Docs: https://wemep.readthedocs.io/en/latest/index.html
.. _Community Guide: https://wemep.readthedocs.io/en/latest/community/index.html

License
-------
`GNU General Public License`_ v3.0 © 2019 Windbench

.. _GNU General Public License: LICENSE