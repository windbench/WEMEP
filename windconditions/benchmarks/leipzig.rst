Leipzig Neutral ABL Profile
===========================

Status
------
.. admonition:: June 2014

   The Leipzig benchmark was developed in Wakebench Phase 1. The results were presented at the Torque 2014 conference.

	   * `Verification data <https://doi.org/10.5281/zenodo.4090378>`_ :cite:`javier_sanz_rodrigo_verification_2012`
	   * `Presentation <https://doi.org/10.5281/zenodo.4088287>`_ :cite:`rodrigo_presentation_task31_torque_2014`
	   * `Paper <https://iopscience.iop.org/article/10.1088/1742-6596/524/1/012105>`_ :cite:`rodrigo_task31_torque_2014`

   **Highlights**

   :numref:`fig-leipzig-neutral` shows two RANS and one LES simulations. Both RANS models use a length-scale limiter (:math:`\lambda \approx 42 m`) to monotonic linear growth of the mixing legth with height that surface-layer models would predict. Both RANS simulations differ in the value of :math:`\lambda` but produce results consistent with the Leipzig data. The LES results show too much mixing in the upper part of the boundary layer resulting in too deep boundary layer.

	.. _fig-leipzig-neutral:
	.. figure:: ../../_static/windconditions/benchmarks/leipzig_neutral.png
	    :width: 600
	    :align: center

	    Leipzig neutral profiles for non-dimensional wind speed, wind shear and eddy viscosity. `© Author(s) 2014. CC BY 3.0 License <https://iopscience.iop.org/article/10.1088/1742-6596/524/1/012105>`_. Used with permission. :cite:`rodrigo_task31_torque_2014`   


Scope and Objectives
--------------------
The case is suitable for the verification of ABL models in neutral conditions. The objective is to demonstrate how ABL models reproduce the characteristic Ekman spiral driven by uniform geostrophic forcing.

Background
----------
The measurements were done on a grass-covered airfield with flat surroundings. Upstream, the air passes over the city of Leipzig. The Leipzig wind profile results from a set of 28 pitot-balloon observations with two theodolites, between 9:15 and 16:15 on October 20, 1931, during stable weather :cite:`mildner_1932`. During the experiment, the surface isobars were rectilinear indicating that the geostrophic conditions were steady and the horizontal gradients were negligible. 

Lettau (1950) :cite:`lettau_re-examination_1950`, performed a reanalysis of the measurements which resulted in a smooth profile, a "representative average" of the original, more scattered data. This classical profile has been discussed extensively in the literature. The boundary layer meteorology folklore considers this profile as a reference for an idealized neutral, barotropic (geostrophic wind constant with height), horizontally homogenous steady-state atmospheric boundary layer (ABL). However, it has been also argued that the profile was obtained in slightly stable conditions with an Obukhov length in the order of 500 m obtained by profile fitting in the lower 150 m :cite:`sundararajan_aspects_1979`. In fact, Lettau (1950) reports a lapse rate of potential temperature of 0.35 K / 100 m.

The Leipzig wind profile has been extensively used for the analysis and design of ABL models. Blackadar (1962) :cite:`blackadar_vertical_1962` derived his well known analytical expression for the ABL mixing length profile in flat terrain making use of this profile. The limiting value of the mixing length was found to be proportional to the ratio of the geostrophic wind and the Coriolis parameter. He assumed that the slight stratification of the profile did not influence its turbulence structure. Many mixing-length models of the ABL are based on Blackadar's parameterization ever since. 

Detering and Etling (1985) :cite:`detering_application_1985` proposed a k-ε model of the ABL that could reduce the excessive mixing of the default turbulence model of Launder and Spalding (1974) :cite:`launder_numerical_1974`. A similar strategy was followed by Apsley and Castro (1997) :cite:`apsley_limited-length-scale_1997` using a length-scale limiter to avoid the quasy-linear growth of the mixing length beyond the surface layer.

Riopellle and Stubley (1989) :cite:`riopelle_influence_1989` used a second-order turbulence closure that included stable stratification and found better agreement with the Leipzig profile than if neutral conditions were assumed.    

Even though it is quite old, the Leipzig profile is useful because of the steady barotropic conditions of the experiment. Being a well-established reference, it is suitable for verification and model intercomparison studies. However, since the dataset does not include thermal stratification properties, it should not be treated as a complete model validation dataset.   

Input Data 
----------
The conditions for simulating the Leipzig wind profile in neutral conditions are:

* Geostrophic wind: :math:`U_g = 17.5 m s^{-1}`, :math:`V_g = 0`
* Coriolis parameter: :math:`f_c = 1.13e-4 s^{-1}`
* Roughness length: :math:`z_0 = 0.3 m`
* Obukhov length: :math:`L = \infty`

Use dry air with a density :math:`\rho = 1.225 kg m^3` and dynamic viscosity :math:`\mu = 1.73e-5 kg m^{-1}s^{-1}`

Validation Data
---------------
The validation data consists on vertical profiles of velocity components and eddy viscosity as estimated by Lettau (1950) :cite:`lettau_re-examination_1950`. They can be found in this data repository: :cite:`javier_sanz_rodrigo_input_2012`

Model Runs
----------
A 3 km high domain shall be used, sufficient to fit the boundary layer height with some margin.

Output Data
-----------
Please provide vertical profiles of velocity components (*U*,*V*), turbulent kinetic energy (*tke*) and turbulent viscosity (*nu_t*) using the file naming and format convention described in the Windbench user's guide with profID = outlet. Hence, the output profile file contains the following variables (header), in this order: Z(m), U(m/s), V(m/s), tke(m2/s2), nu_t(m2/s).

Remarks
-------
This benchmark is based on prescribed boundary conditions in order to evaluate the scatter of different ABL models. You can try to guess the stability conditions by running a quasi-steady stratified case and uniform cooling.  

References 
----------
.. bibliography:: leipzig_references.bib
   :all:



