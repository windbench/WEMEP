Contents
========

Introduction
------------
WEMEP addresses quality assurance of models being used for research and to drive wind energy applications. This is achieved through a framework to conduct formal verification and validation (V&V) that ultimately determines how model credibility is built upon. Based on the AIAA guide for V&V of computational fluid dynamics (CFD) :cite:`AIAA_1998`: 

* **Verification** is the process of determining that the model implementation accurately represents the developer’s conceptual description of the model and the solution of the model. Here accuracy is measured with respect to benchmark solutions of simplified model problems

* **Validation** is the process of determining the degree to which the model is an accurate representation of the real world from the perspective of the intended uses of the model. Here accuracy is measured with respect to experimental data.

The AIAA guide states that verification and validation are processes or ongoing activities without a clearly defined completion point. It is a matter of performing as many V&V exercises as possible in order to gain confidence and credibility on the model results towards the specific intended use of the model. Indeed, the *intended use*, i.e. the target application, is the main driver of this process to define the physical scope of the design system, its range of operating conditions, the variables of interest and their associated acceptance criteria. By identifying the needs from the application point of view, it is possible to define a validation plan, built on existing benchmarks, to foresee the most relevant experimental knowledge gaps.

The intrinsic high complexity of the wind energy design system makes it very difficult to validate the full range of operating conditions. Hence, the main objective of the validation process is to develop and quantify enough confidence on the computer model (or code) so that they can be used reliably to predict the variables of interest within acceptable limits. Hence, validation is sometimes also referred to the assessment of the *predictive capacity* of a code.       

WEMEP is based SANDIA's **V&V Framework** :cite:`Hillsetal_2015` which, itselft, is based on well-established procedures developed by various organizations including the Department of Energy, National Aeronautics and Space Administration, the American Institute of Aeronautics and Astronautics, and the American Society of Mechanical Engineers. Background articles include :cite:`Oberkampf&Trucano_2002`, :cite:`Oberkampfetal_2004` and :cite:`Oberkampf&Barone_2006`. The framework's primary focus is *to provide guidance on the development and execution of tightly integrated modeling/experimental programs based on well-established V&V practices for the purpose of model assessment*.

Based in Europe, it is also worth mentioning the **COST-732 Model Evaluation Guidance and Protocol Document** :cite:`Britter&Schatzmann_2007` with focus on microscale modeling for the dispersion of pollutants in the urban environment. The protocol comprises the following aspects:

* A scientific evaluation process, that considers the formulation of the models in terms of physics included and the degree of suitability for the intended use. 
* A verification process that addresses both the code (consistency with the conceptual model) and the solution procedure (to estimate the numerical error)
* The provision of appropriate and quality assured validation datasets. 
* A model validation process in which model results are compared with experimental datasets.
* An operational evaluation process that reflects the needs and responsibilities of the model user.

Quoting COST-732, *models of whatever type are only of use if their quality (fitness-for-purpose) has been quantified, documented, and communicated to potential users* :cite:`Britter&Schatzmann_2007`. Hence, WEMEP will define the framework that wind energy model developers can follow to make their codes trustfull for the wind energy community. Trust is built when the code performance has been tested and quantified based on appropriate datasets agreed upon to cover a relevant range of applicability. This protocol shall also support the planning, setting up and execution of forthcoming experiments that will feed the validation process as a sistematic and sustained activity for model development. 


Scope and Objectives
--------------------


Terminology
-----------


Quick Guide
-----------

Identify the Challenge
^^^^^^^^^^^^^^^^^^^^^^

Scientific review
^^^^^^^^^^^^^^^^^

Find a Suitable Validation Database
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Assess the Validation Hierarchy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A/B Testing
^^^^^^^^^^^

Quantify Performance for Intended Use
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Identify Knowledge Gaps
^^^^^^^^^^^^^^^^^^^^^^^


Validation Directed Program 
---------------------------

Setting goals based on quantities of interest and metrics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Defining priorities based on Phenomena Identification Ranking Table (PIRT) gap analysis
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Verification
------------

Code Verification
^^^^^^^^^^^^^^^^^

Solution Verification
^^^^^^^^^^^^^^^^^^^^^


Validation
----------

Defining a validation strategy using a building-block hierarchy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Design of experiment
^^^^^^^^^^^^^^^^^^^^

Setting up of a validation benchmark
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Validation assessment at system level 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Uncertainty Quantification
--------------------------

Aleatory and epistemic uncertainty 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sources of uncertainty
^^^^^^^^^^^^^^^^^^^^^^

Experimental uncertainty
^^^^^^^^^^^^^^^^^^^^^^^^

Computational model uncertainty
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Blind Testing 
-------------

Blind Testing
^^^^^^^^^^^^^

Model Calibration
^^^^^^^^^^^^^^^^^


Documenting
-----------


Data Provision
--------------

Data Provision
^^^^^^^^^^^^^^

Licensing
^^^^^^^^^


References
----------
.. bibliography:: references.bib
	:all:


