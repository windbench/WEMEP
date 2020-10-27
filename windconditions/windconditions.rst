Wind Conditions 
===============

Wind conditions is a generic term to refer to atmospheric flow quantities that affect wind turbine and wind farm performance in terms of energy production and structural integrity. This is the context for the application of atmospheric flow models in activities such as wind resource and energy yield assessment, wind turbine site suitability and wind farm design, during the planning phase, and weather and wind power forecasting during the operational phase of the wind farm. The IEA-Wind TCP Task 31 `Wakebench <https://community.ieawind.org/task31/home>`_ is focused on the planning phase while `Task 36 <https://www.ieawindforecasting.dk/>`_ is dealing with wind power forecasting. The model evaluation framework shall focus on the wind farm system, considering all the mesoscale-to-microscale weather and turbulence processes, which are relevant for inflow and wind farm wake propagation and interaction.   

Intended Use
------------

Assessment of Wind Resource, Energy Yield and Turbine Suitability
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The assessment of the long-term wind resource, energy yield and turbine site suitability is addressed by the `IEC 61400-15 working group <https://www.iec.ch/dyn/www/f?p=103:14:13217413763586::::FSP_ORG_ID:10314>`_ by providing a framework for assessment and reporting. Two standards result from this group: 

* The IEC 61400-15-1 complements IEC 61400-1 and 61400-3 in the reporting of site specific wind conditions and related atmospheric variables. 
* The IEC 61400-15-2 addresses the asessment and reporting of wind resource and energy yield.

Whenever possible we shall use the definitions provided therein on relevant quantities of interest for flow model evaluation. The variables are integrated with a wind speed distribution that is representative of the design lifetime and they are defined at hub-height (:math:`z_{hub}`) unless otherwise stated.

.. note:: 
   As of June 2020, the IEC 61400-15 standards are in draft form.  

Wind Resource
"""""""""""""
* *Annual average wind speed at hub height* (:math:`V_{ave}`): wind speed averaged according to the definition of *annual average*, i.e. mean value of a set of measured data of sufficient size and duration to serve as an estimate of the expected value of the quantity. The averaging time interval shall be a whole number of years to average out non-stationary effects such as seasonality.  

* *Annual wind speed frequency distribution* (:math:`f_{i,j}`): Annual distribution of wind speeds as a function of wind direction *i* and/or wind speeds *j*. Wind speed is classified using 1 m/s bins and wind direction sectors are no wider than :math:`30^{\circ}`. Additional dimmensions related to turbulence characteristics like stability, turbulence intensity or wind shear could be used for additional granularity in the distribution.  

* *Weibull distribution*: The probability distribution function used to describe the distribution of wind speeds over a period of one year, defined in terms of the scale parameter (:math:`C`) and shape parameter :math:`k`.

  .. math:: P_w(V) = 1 - exp\left[-(V/C)^k\right]


Energy Yield
""""""""""""
* *Gross annual energy production* (:math:`AEP_{gross}`): total amount of electrical energy produced by the Wind Turbine Generator System (WTGS), estimated by integrating the power curve with the wind speed frequency distribution and multiplying by the number of hours in a year. For a wind farm:

  .. math:: AEP_{gross} = T\sum_{i,j,k} P_k(V_j) f_{i,j,k}

  where :math:`f_{i,j,k}` is the annual wind speed frequency distribution at each turbine site *k*, :math:`P_k(V_j)` is the power curve of each turbine at wind speed :math:`V_j` and :math:`T` = 8760 h is the number of hours in a year. The gross AEP is also defined as the AEP at a reference site, typically a meteorological mast, vertically extrapolated to hub-height and horizontally extrapolated to the turbine sites. This extrapolation is carried out by profile methods and flow models that predict speed-up effects due to terrain elevation and roughness changes, forest canopies and obstacles. 

* *(Net) Annual energy production* (:math:`AEP`): total amount of electrical energy delivered at the grid connection point after deducing all the energy losses that take place in the wind farm. 

  .. math:: AEP = AEP_{gross} - AEP_{gross}\prod_{l} \eta_{l} 

  where :math:`\eta_{l}` is the *efficiency* corresponding to the loss category *l* as per the IEC 61400-15, namely: electrical, availability, wake effect, curtailment, environmental and turbine performance. Each category includes a number of subcategories. For instance, wake losses are subdivided into internal (interarray effects), external (current farm-farm effects) and future (prospect farm-farm effects) wake losses. Internal wake losses are predicted by wake models to obtain the, so-called, *array efficiency*:

  .. math:: \eta_{wake} = \frac{P_{wake}}{P_{gross}} = \frac{\sum_{i,j,k} Pw_k(V_j) f_{i,j,k}} {\sum_{i,j,k} P_k(V_j)f_{i,j,k}}

  where the efficiency is defined in terms of a power ratio with :math:`Pw_k` being the power output predicted by the wake model at each turbine position *k*.

* *Annual capacity factor* (:math:`CF`): the ratio between the AEP and the maximum possible annual energy output, an ideal case where all turbines would be producing at rated power throughout the year.    

  .. math:: CF = \frac{AEP}{T\sum_{k} Prated_k}

  where :math:`Prated_k` is the rated power of each turbine. Alternatively, wind farm performance is defined in terms of the *annual equivalent hours* of the wind farm operating at rated power, i.e. :math:`AEH = CF \cdot T`

The pre-construction energy yield assessment process will output a distribution of AEP defined in terms of the median :math:`P50`, where the actual AEP would be exceeded 50% of the time, and a standard deviation :math:`\sigma_{AEP}` as a measure of the AEP *uncertainty*. Then, the *prediction bias* is the difference between the estimated *P50* and the actual AEP

.. math:: BIAS_{AEP} = AEP_{true} - AEP_{P50} 

While each quantity of interest can be subject to uncertainty quantification individually, the main focus of the IEC 61400-15-2 standard is to predict the overall energy production uncertainty since this is directly connected to the financial performance of a wind project. This overall uncertainty is broken down into categories and subcategories by the standard to provide a common framework for the wind industry. Lee and Fields (2020) :cite:`lee_overview_2020` provide a review of energy yield assessment prediction bias, losses and uncertainties following this framework. The review shows that while there has been a tendency towards the overestimation of P50, this has been progressively corrected and we are now approaching zero bias on average. The estimated mean AEP uncertainty remains at over 6% implying that there is room for improvement. Indeed, changing the uncertainty by 1% can lead to 3-5% change in the net present value of a wind farm :cite:`lee_overview_2020`.  

Site Suitability
""""""""""""""""
* *Extreme wind speed with a recurrence interval of 50 years* (:math:`V_{50}`): Also called *reference wind speed* (:math:`V_{ref}`) in the IEC 61400-1 standard to define WTGS classes. A turbine designed for a WTGS class with a reference wind speed :math:`V_{ref}`, is designed to withstand climates for which the extreme 10 min average wind speed with a recurrence period of 50 years at turbine hub-height is lower than or equal to :math:`V_{ref}`.  

* *Annual average flow inclination angle* (:math:`\phi`): The flow inclination is defined as the angle between a horizontal plane and the wind velocity vector at hub height: 

  .. math:: \phi = tan^{-1}\left(V_z/V_{xy}\right) 

  where :math:`V_{xy}` and :math:`V_{z}` are the horizontal and vertical components of the wind speed. The flow inclination angle is positive if the wind velocity vector is pointing upwards. The annual average shall be taken as the energy weighted mean from all directions.

* *Mean turbulence intensity* (:math:`I`): the ratio of the wind speed standard deviation to the mean wind speed determined from the same set of measured wind speed data and taken over a period of 10 minutes and a minimum sampling frequency of 5 seconds.

  .. math:: I = \frac{\sigma_V}{V}

* *Standard deviation of turbulence intensity* (:math:`\sigma_{I}`): The standard deviation of a sub set of the turbulence intensities (:math:`I`). The sub set typically represents a bin within a wind speed- wind direction matrix.

* *Average turbulence intensity at 15m/s* (:math:`I_{15}`): Mean turbulence intensity over all wind directions in 15m/s wind speed bin.

* *Extreme ambient turbulence intensity*: Extreme value of the ambient turbulence intensity with a return period of 50 years as a function of wind speed.   

* *Mean wind shear* (:math:`\alpha`): Wind shear, i.e. the variation of wind speed across a plane perpendicular to the wind direction, (or power law) exponent.

  .. math:: V(z) = V(z_r)\left(\frac{z}{z_r}\right)^{\alpha}

Numerical Site Calibration
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. todo:: Define end-user requirements explicitely. 

   * Discuss IEC 61400-12-4 context 
   * Scope and Objectives
   * Definitions of Quantities of Interest
   * Impact of bias and uncertainty: set quality acceptance criteria


Multi-Scale Modeling of Wind Conditions
---------------------------------------
Sanz Rodrigo et al. (2016) :cite:`rodrigo_mesoscale_2017` provide a review of mesoscale-to-microscale wind farm flow models of different fidelity levels considering meteorological and wind energy terminology. Each scale has different applications and quantities of interest, which will determine the orientation of the model evaluation strategy (:numref:`fig-model-chain`). 

.. _fig-model-chain:
.. figure:: ../_static/windconditions/model-chain.png
    :width: 600
    :align: center

    Model-chain for wind farm flow modeling. `© 2016 John Wiley & Sons, Ltd <https://onlinelibrary.wiley.com/doi/pdf/10.1002/wene.214>`_. Used with permission. :cite:`rodrigo_mesoscale_2017`

Models can be coupled together to form a multi-scale modeling system where, for instance, the microscale sub-system (the wind farm) uses input data generated by the mesoscale sub-system to characterize the long-term wind climate distribution that modulates the local wind conditions. Similarly, an aerolastic model of the turbine sub-system can be used to predict detailed rotor aerodynamics responsible for wake generation in the wind farm wake model. A mind map elaborated during IEA-Task 31 Phase 3 shows the relationships between model building-blocks at different scales, input quantities and phenomena of interest for the intended use of these models (:numref:`fig-windconditions-mindmap`). 

.. _fig-windconditions-mindmap:
.. figure:: ../_static/windconditions/mindmap/map.svg
    :width: 600
    :align: center

    Mind map of multi-scale models and phenomena of interest for wind conditions.
    `Interactive mind map <../_static/windconditions/mindmap/index.html>`_  

The mind map breaks down the full complexity of atmospheric models into three scales:

1. **Global**: drives wind climate variability from seasons to decades at horizontal scales of tens of kilometers. Global reanalyses are typically used to characterize this variability and serve as input boundary condtions for mesoscale models. 
2. **Mesoscale**: drives weather processes at regional level down to scales of the order of 1 km. Relevant mesoscale phenomena include: horizontal wind speed (gross AEP) gradients due large-scale topography, land-sea transitions and farm-farm (external wake) effect, low-level jets producing large wind shear during stable conditions, etc. Mesoscale models provide forcing for microscale models in the form of virtual masts, generalized wind climates, lateral boundary conditions or volumetric forzes (also called tendencies).  
3. **Microscale**: drives turbulence and speed-up effects at site level at scales down to a few meters. Site effects depend on local changes in elevation and roughness, the presence of obstacles and forest canopies as well as thermal stratification across the atmospheric boundary-layer (ABL). Microscale effects are particularly important in complex terrain where relevant phenomena develop such as: flow separation and recirculation, gravity waves, gap flow, hydraulic jump, mountain-valley winds, etc. At microscale, wind farm wake models are embedded in atmospheric flow models to simulate internal wake effects that determine array efficiency. 

Wake models are described in detail in the :ref:`Multi-Scale Wind Farm Modeling` section to simulate external and internal wake effects (array efficiency) and wind turbine loads. 

Validation Strategy
-------------------
Following the model evaluation process of :numref:`fig-ambidextrous-process`, a validation strategy for wind conditions requires the provision of high-fidelity experiments targeting high-impact phenomena of interest, to validate the capacity of the flow model to deal with relevant physics, as well as long-term wind resource campaigns to demonstrate the added value that resolving these phenomena brings to the applications of interest. These applications typically involve integrating a discrete number of flow model simulations with a statistical methodology that provides the expected long-term mean or extreme values and the associated uncertainties. This should be done for a wide variety of wind climates and siting conditions to cover the widest operational range possible. 

This validation strategy was implemented in the `New European Wind Atlas <https://zenodo.org/communities/newa/?page=1&size=20>`_ (NEWA) project towards the development of a new methodology for the assessment of wind conditions that is based on a mesoscale to microscale model-chain approach :cite:`rodrigo_new_2020`. The scope of the project was focused on wind conditions for wind resource and site assessment, i.e. without the influence of wind turbines. Therefore, the model-chain was devoted to atmospheric flow models with two applications in mind:

* **Wind atlas for regional planning**: the main focus was on the mesoscale model, to come up with a reference set-up of the Weather Research and Forecasting (WRF) model that could be used seamlessly across Europe. Through sensitivity analysis, the most suitable configuration was selected to produce a 30-year long simulation forced by ERA5 reanalysis data :cite:`hahmann_making_2020`. Then, this long-term wind climate was statistically downscaled to 50 m using the WAsP methodology. Hence, the wind atlas model-chain consists on physical downscaling down to 3 km resolution, to produce long-term time series of mesoscale wind characteristics, whose long-term wind climate distributions are then used as input data for a microscale model to produce high-resolution wind resource quantities. The validation strategy was based on a database of 291 meteorological masts, at least 40 m tall, made available by Vestas :cite:`dorenkamper_making_2020`. The main objective of the validation campaign was to determine the general quality of the wind atlas, categorized by regions and terrain complexity, determined by the ruggedness index *RIX* (:numref:`fig-NEWA-windatlas-validation`) :cite:`mortensen_field_2008`. A one year multi-physics ensemble run was also used to quantify the spread of mesoscale winds which would translate into input uncertainty for microscale models :cite:`f_gonzalez_rouco_report_2019`.       

.. _fig-NEWA-windatlas-validation:
.. figure:: ../_static/windconditions/NEWA_windatlas_validation.png
    :width: 600
    :align: center

    Distributions of mean gross power bias, using the NREL 5MW reference turbine power curve, for the various stages of the NEWA model chain grouped by ruggedness index (RIX) category: low (a), medium (b), high (c), and all of the samples combined (d). `© Author(s) 2020. CC BY 4.0 License <https://gmd.copernicus.org/preprints/gmd-2020-23/>`_. Used with permission. :cite:`dorenkamper_making_2020`  

* **Site assessment**: here the main focus was on the microscale model, in particular, in the implementation of mesoscale forcing and boundary conditions for heterogeneous topography (complex terrain and forest canopies) using both Reynolds-Averaged Navier Stokes (RANS) and Large-Eddy Simulation (LES) turbulence models. Hence, the validation strategy seeked validation cases from detailed experiments where these modeling feutures would be tested in the prediction of mean flow and turbulence quantities. The range of experiments carried out in the NEWA allows testing over a wide range of siting conditions from offshore to coastal transitions to smooth and complex terrain with a without forest canopies. Next section provides an overview of these experiments and other open-access datasets that can be used to validate flow models.         

Experiments and other Observational Datasets  
--------------------------------------------
The building-block validation hierarchy of :numref:`fig-windconditions-building-blocks` provides a framework to map validation datasets with phenomena of interest at different scales and show how they complement each other to cover a reasonably wide range of wind conditions. Site effects are modulated by the regional wind climate which is driven by synoptic weather and local mesoscale processes.    

.. _fig-windconditions-building-blocks:
.. figure:: ../_static/windconditions/windconditions-building-blocks.png
    :width: 600
    :align: center

    Building-block validation hierarchy and phenomena of interest for wind conditions.

While long-term statistics of wind conditions are traditionally characterized with meteorological masts, many recent experiments include an intense operational period (IOP) of several weeks to months with extensive use of remote sensing equipment. In particular, scanning lidar systems allow to characterize the spatio-temporal structure of the flow field along  scanning trajectories following a particular transect, or slicing vertical or horizontal planes (:cite:`mann_complex_2017`). :numref:`tab-windconditions-datasets` provides a summary of experiments and other sources of open-access data for the validation of atmospheric flow models. 

.. _tab-windconditions-datasets:
.. table:: Summary of open-access datasets for the validation of flow models for wind conditions
   :class: longtable

   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | Dataset            | Location    | Period               | Site Conditions         | Key References & Repositories                                      |
   +====================+=============+======================+=========================+====================================================================+
   | **Homogeneous ABL**                                                                                                                                    |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Cabauw*           | This 200-m tall mast has been a reference in ABL research for its horizontally homogeneous conditions.                            |
   |                    | The GABLS3 flow case is a diurnal cycle developing a strong nocturnal low-level :cite:`bosveld_third_2014a`.                      |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Netherlands | Since 2008           | Flat terrain            | `Cesar Database <https://ruisdael-observatory.nl/cesar-database/>`_|
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Coastal and Offshore**                                                                                                                               |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Fino 1,2,3*       | Three 100-m tall offshore research platforms measuring boundary layer measurements between 30 and 100 m.                          |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | North and   | Since 2003           | Offshore                | `FINO1,2,3 <https://www.fino-offshore.de/>`_,                      |
   |                    | Baltic Seas |                      |                         | `BSH Database <http://fino.bsh.de/>`_                              |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Satellite SAR*    | Satellite SAR wind data archive from 2002                                                                                         |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Global      | Since 2002           | Offshore                | `DTU Satellite Winds <https://satwinds.windenergy.dtu.dk/>`_       |
   |                    |             |                      |                         | :cite:`hasager_europes_2020`                                       |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *RUNE*             | Near-shore wind resource from 8 lidars, one ocean buoy and satelite data                                                          |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Denmark     | 2015-11 to 2016-02   | Near-shore              |  :cite:`floors_rune_2016`                                          |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Ferry Lidar*      | Offshore wind resource from a ferry-mounted profiling lidar (65-275 m) along the South Baltic Sea from Kiel (Germany) to          |
   |                    | Klaipeda (Lithuania).                                                                                                             |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Baltic Sea  | 2017-02 to 2017-06   | Offshore                | :cite:`gottschall_newa_2018`                                       |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Roughness Changes and Canopies**                                                                                                                     |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Ryningsnäs*       | 200-m tall mast in a patchy forested site in simple terrain conditions                                                            |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Sweden      | 2011-10 to 2012-06   | Forested simple terrain | :cite:`arnqvist_wind_2015`, :cite:`arnqvist_investigation_2019`    |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Østerild*         | Two horizontally scanning Doppler lidars, mounted on 250-m high masts and measuring at 50 and 200 m the flow above patchy         |
   | *Balconies*        | forest                                                                                                                            |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Denmark     | 2016-04 to 2016-08   | Forested flat terrain   |  :cite:`karagali_new_2018`                                         |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Isolated Hill**                                                                                                                                      |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Askervein*        | 116 m high smooth hill isolated in all wind directions but the NE-E sector. Over 50 masts installed, 35 of them of 10 m           |
   |                    | height installed along transects following the main axes of the hill                                                              |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Scotland    | 1982/1983            | Smooth hill             | :cite:`taylor_askervein_1987`, :cite:`taylor_askervein_1983`       |
   |                    |             |                      |                         | :cite:`taylor_askervein_1985`                                      |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Rödeser Berg*     | 200-m tall forested hill equipped with a 200-m mast at the hill top, a 140-m mast at the inflow and scanning Doppler lidars       |
   | *(Kassel)*         | mapping a transect along the prevailing wind direction                                                                            |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Germany     | 2016-10 to 2017-01   | Forested hill           | :cite:`dorenkamper_large-eddy_2019`                                |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Undulating Terrain**                                                                                                                                 |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Hornamossen*      | 10-km long transect consisting of 9 remote sensing profilers and one 180-m flux-profile mast in forested and moderately           |
   |                    | complex terrain. Surface pressure gradient measurements                                                                           |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Sweden      | 2015-06 to 2017-07   | Forested rolling hills  | :cite:`mann_complex_2017`                                          |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Steep Ridges**                                                                                                                                       |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Bolund*           | 12-m high hill surrounded by water in all directions except to the E. An almost vertical escarpment faces the prevailing W-SW     |
   |                    | sector. 10 masts equiped with sonic and cup anemometers.                                                                          |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Denmark     | 2007-2008            | Small isolated ridge    | :cite:`bechmann_bolund_2009`, :cite:`berg_bolund_2011`,            |
   |                    |             |                      |                         | :cite:`bechmann_bolund_2011`                                       |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Perdigão*         | 50 masts, 20 scanning lidars, 7 profiling lidars and other meteorological equipment distributed along and across two parallel     |
   |                    | steep ridges.                                                                                                                     |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Portugal    | 2016-12 to 2017-06   | Double ridge            | `FEUP-Porto Database <http://perdigao.fe.up.pt/>`_,                |
   |                    |             |                      |                         | `NCAR Database <https://data.eol.ucar.edu/project/Perdigao>`_,     |
   |                    |             |                      |                         | :cite:`fernando_perdigao_2019`                                     |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | **Mountaineous complex terrain**                                                                                                                       |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   | *Alaiz*            | 5 scanning Doppler lidars measuring a Z-shaped 10-km long transect along the ridge tops and across the valley together            |
   | *(ALEX17)*         | with a windRASS profiler, 7 tall masts and 10 surface stations                                                                    |
   +                    +-------------+----------------------+-------------------------+--------------------------------------------------------------------+
   |                    | Spain       | 2017-07 to 2019-07   | Ridge-valley-mountain   | :cite:`cantero_alaiz_2019`, :cite:`santos_alaiz_2019`,             |
   |                    |             |                      |                         | :cite:`santos_alaiz_2020`                                          |
   +--------------------+-------------+----------------------+-------------------------+--------------------------------------------------------------------+

.. note::
   Other open-access datasets can be added when they have been used for flow model validation (provide references) 

Phenomena of Interest 
---------------------
.. todo:: Most recent PIRT addressing relevent phenomena for wind conditions. 

   * List of physical phenomena providing definitions and references 
   * PIRT table from MMC

.. _benchmarks_phenomena:

Benchmarks on Flow Phenomena 
----------------------------
Following the building-block approach illustrated in :numref:`fig-windconditions-building-blocks`, we provide a comprehensive list of benchmarks for the design and testing of atmospheric flow models. These test cases are derived from theory and high-fidelity experiments to target specific flow phenomena that is considered relevant for the intended uses of the models. From Monin-Obukhov theory in homogeneous conditions to flow over complex terrain and forest canopies, a hierarchy of flow cases is provided in each building-block.   

The Homogeneous Atmospheric Boundary Layer (ABL)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The ABL building-block of :numref:`fig-ABL-building-block` deals with the horizontally homogeneous atmospheric boundary-layer. A hierarchy of verification and validation cases is suggested to progressively incorporate essential physics, namely:

1. *Monin-Obukhov similarity theory* (MOST) for **surface-layer steady-state** conditions depending on roughness and stability :cite:`monin_obukhov_1954`. 
2. *Leipzig* **ABL** wind profile in **neutral** steady-state conditions :cite:`lettau_re-examination_1950`.
3. *GABLS1* **stable ABL** under uniform geostrophic wind and surface cooling :cite:`cuxart_single-column_2006`. 
4. *GABLS2* **diurnal cycle** under uniform geostrophic wind and varying surface temperature :cite:`kumar_impact_2010`.
5. *GABLS3* diurnal cycle under **realistic mesoscale forcing** and varying surface boundary conditions :cite:`bosveld_third_2014a`. 
6. *Cabauw* **annual integration** of the wind climate to predict quantities of interest for the intended use wind resource assessment and turbine siting :cite:`rodrigo_comparing_2018` (see :ref:`apps-wra` section).

.. _fig-ABL-building-block:
.. figure:: ../_static/windconditions/ABL-building-block.png
    :width: 600
    :align: center

    V&V hierarchy for the ABL building-block.

Benchmarks for *MOST* and *Leipzig* were conducted during Wakebench Phase 1 :cite:`rodrigo_iea-task_2014`. The GEWEX Atmospheric Boundary Layer Studies (*GABLS*), developed by the boundary-layer meteorology community :cite:`holtslag_stable_2013`, can be adopted by the wind energy community by focusing the evaluation on rotor-based quantities of interest :cite:`sanz_rodrigo_methodology_2017`. The *GABLS3* and *Cabauw* benchmarks were conducted in Wakebench Phase 2 :cite:`rodrigo_results_2017`:cite:`rodrigo_comparing_2018`. 

.. toctree::
   :glob:
   :maxdepth: 1

   benchmarks/MOST.rst
   benchmarks/leipzig.rst
   benchmarks/gabls3.rst

Coastal-Offshore
^^^^^^^^^^^^^^^^
The marine atmospheric boundary layer is formed through exchanges of momentum moisture and heat across the air-sea interface. :numref:`fig-cblast` shows a schematic of the physical processes that take place in the coupled atmospheric-ocean boundary layer :cite:`edson_coupled_2007`. Mesoscale variability and wave-induced effects produce deviations from land-based turbulence spectra and flux-profile relationships used in ABL parameterizations :cite:`smedman_case_1999`. The coastal region, where most offshore wind energy is deployed, is subject to large mesoscale variability influenced by coastal topography and temperature gradients between land and sea :cite:`dorenkamper_offshore_2015`. These heterogeneous conditions generate important **horizontal wind speed gradients** breaking MOST assumptions on which many wake models are based. Furthermore, frequent **stable conditions** develop due to large land-see temperature contrast producing large-shear **low-level jets (LLJ)** in shallow boundary-layers and **gravity waves** that increase wind farm global blockage :cite:`allaerts_gravity_2018`. In **extreme wind** conditions, wave-induced shear-stress becomes dominant favouring the use of a  wind-wave coupled model :cite:`larsen_estimation_2019`.   

.. _fig-cblast:
.. figure:: ../_static/windconditions/cblast.jpg
    :width: 600
    :align: center

    Air-sea interaction processes in the marine boundary layer. `© American Meteorological Society <https://journals.ametsoc.org/bams/article/88/3/341/59046/The-Coupled-Boundary-Layers-and-Air-Sea-Transfer>`_. Used with permission. :cite:`edson_coupled_2007`

The NEWA project has produced two benchmarks suitable for the assessment of the coastal-offshore boundary layer. The *Ferry-Lidar* experiment consist on following a ferry-mounted profiling lidar, for a period of 4 months, along a regular route in the Southern Baltic Sea between Kiel (Germany) and Klaipeda (Lithuania). The RUNE experiment comprises measurements from 8 lidars and a buoy to measure the evolution of the wind speed along a ~8 km fetch.   

.. toctree::
   :glob:
   :maxdepth: 1

   benchmarks/ferry-lidar.rst

.. todo:: 
   * Complete Ferry-Lidar benchmark. 
   * Add RUNE benchmark.

Forest Canopy
^^^^^^^^^^^^^
A canopy is considered when the roughness elements over the ground surface are of significant size compared to the height of interest (e.g. hub-height). Here we shall focus on forest canopies although the term could be also applied for a urban canopy or a wind farm canopy. The classical interpretation of the flow over a forest canopy is that of a displaced logarithmic profile originating by the momentum absortion through aerodynamic drag across the depth of the canopy :cite:`kaimal_finnigan_1994`, where the **displacement height** depends on the distribution of the drag through the foliage. Within the canopy the flow is highly turbulent and heterogeneous which prevents us from extending MOST to the canopy layer as if it was a rough lower boundary. A more realistic approach requires to model explicitely the distribution of drag and the energy balance between the surface and the air aloft to characterize the flow above and within the canopy. 

The structure of the turbulent flow in horizontally homogeneous canopies have been the object of study of numerous experiments ranging from wind tunnel models (e.g. :cite:`brunet_wind_1994`) to tall forests :cite:`kaimal_finnigan_1994`. All the profiles display a characteristic inflexion point near the canopy top which separates the canopy flow from the boundary layer profile above. A constant shear stress region is present in the free-stream which decreases rapidly as momentum is absorbed by the canopy. 


**Heterogeneous forest canopies** combine patches of trees of different heights and foliage density that typically change throughout the year. Aerial lidar scans are used to map the tree height and plant area density :cite:`boudreault_lidar_2015`. Highly heterogeneous conditions happen at **forest edges** as the flow transitions through an internal boundary layer towards a developed canopy boundary layer :cite:`dellwik_flow_2014` :cite:`boudreault_how_2017`.

The *Ryningsnäs* experiment was used in the NEWA project to validate ABL models in neutral conditions :cite:`ivanell_micro-scale_2018` considering mean vertical profiles of wind speed and turbulence intensity for different wind direction sectors. A follow-up experiment, *Hornamossen*, studied the mean flow along a transect of 9 remote sensing profilers and a reference 180-m met mast over undulated forested terrain :cite:`mann_complex_2017`. The *Østerild Balconies* experiment deployed two horizontally scanning lidars on vertical masts at 50 and 200 m to characterize the heteorogeneous mean flow above the canopy over a relatively flat and semi-forested terrain :cite:`karagali_new_2018`. 

.. toctree::
   :glob:
   :maxdepth: 1

   benchmarks/ryningsnas.rst
   benchmarks/hornamossen.rst

.. todo:: 
   * Complete Ryningsnas and Hornamossen benchmarks. 

.. _isolated-hills:

Isolated Hills 
^^^^^^^^^^^^^^
To study the influence of terrain elevation changes on the ABL we first study the flow over isolated hills, i.e. when the inflow conditions are relatively homogeneous and the height of the hill is small compared to the ABL height (~100 m, where surface-layer turbulence dominates the flow). These conditions have been traditionally used to validate linearized flow models since pioneering work from Jackson and Hunt (1975) :cite:`jackson_turbulent_1975` that led to the *Askervein* experiment in 1982 and 1983 :cite:`taylor_askervein_1987`. This is a 116-m high hill in Scothland with **gentle slopes** (i.e. less than ~30% to prevent flow separation) and homogeneous inflow from the SW, where a quasi-steady flow case in neutral conditions was generated. This case became a golden benchmark to test flow-over-hill models until the *Bolund* hill experiment in 2007 :cite:`bechmann_bolund_2009` :cite:`berg_bolund_2011`: a 12-m high isolated ridge with **steep terrain** in the prevailing wind direction, suitable for testing non-linear flow models still in surface-layer and predominanantly neutral conditions :cite:`bechmann_bolund_2011`. 

The idealized inflow conditions assumed in flow-over-hill studies are suitable for wind tunnel experiments. These are adequate for parametric testing of the flow under different hill shapes, surface roughnesses and stability coditions, e.g. :cite:`finnigan_wind_1990`, :cite:`kim_test_2000`, :cite:`ross_comparison_2004`, :cite:`ross_neutral_2005`, :cite:`wan_large-eddy_2011`. 

The NEWA experiment at the *Röderser Berg* hill near Kassel is the most recent field campaign in the isolated hills category in the wind energy context. This ~200 m hill, **covered by a forest** of 20-30 m tree-heights, includes two 200-m tall masts at the inflow and hilltop and doppler-lidar longitudinal profiles across the hill to measure the speed-up at two heights (80 and 135 m) :cite:`dorenkamper_large-eddy_2019`.  

.. toctree::
   :glob:
   :maxdepth: 1

   benchmarks/askervein.rst
   benchmarks/bolund.rst
   benchmarks/rodeserberg.rst

.. todo:: 
   * Complete Rodeser Berg benchmark. 


Complex Terrain 
^^^^^^^^^^^^^^^
According to the IEC 61400-12-1 standard :cite:`IEC_61400_12_1`, in the context of power performance testing, *complex terrain* is terrain surrounding the test site that features significant variations in topography and terrain obstacles that may cause flow distortion, i.e. significant variations in the wind conditions that affect turbine performance (wind shear, turbulence intensity, etc). To categorize terrain complexity, three types of complex terrain are defined :cite:`IEC_61400_12_1`:

* *Type A*: does not have significant changes in elevation relative to the hub height or particularly steep slopes over long distances. Examples of Type A terrain include gentle rolling hills, and turbine located on a ridge facing a plane. 
* *Type B*: includes mountains, ridgelines, large hills and hilly sites with moderate to steepy sloping terrain and significant changes in elevation relative to the hub height. 
* *Type C*: typically have a steep terrain feature such as a mountain or canyon that may cause flow separation directly upwind of the site of interest. These conditions create drastic changes in wind conditions  

These definitions are relative to the terrain conditions seen at a target wind turbine site and, therefore, depend on the wind direction sector under consideration. 

Terrain complexity has been quantified using the ruggedness index *RIX* which measures the fraction of terrain surface that is steeper than a critical slope of 30-40%. This index is related to the likelihood of **flow separation**, an important factor in the performance of flow models :cite:`mortensen_field_2008`. In effect, the difference between the *RIX* at the reference (measured) site and that at the predicted site, :math:`\Delta RIX` shows positive correlation with the prediction error of a linearized model when the flow is dominated by terrain effects, i.e. without much influence from thermal effects, drastic roughness changes, forest canopy effects or mesoscale effects :cite:`mortensen_field_2008`.      

:numref:`fig-cblast` shows a schematic of the *Perdigão* double-hill experiment illustrating the most relevant physical phenomena :cite:`fernando_perdigao_2019`. While the flow near the surface is dominated by terrain effects, wind conditions at turbine-relevant heights are modulated by mesoscale thermal and (synoptic) topographic forcings. **Thermal circulation effects** due to differences in temperature between the hilltop and the valley cause upslope (anabatic) and katabatic (downslope) winds driven by buoyancy forces. Under synoptic conditions the flow is determined by atmospheric **stability**. In stable conditions, turbulence mixing is reduced mitigating flow separation but favouring the generation of multiple flow phenomena: **lee waves**, **hydraulic jumps**, **shear layers**, **upstream blocking**, etc. In neutral and unstable conditions terrain-induced flow separation is more likely producing **recirculation** in the lee side and other unsteady phenomena due to the interaction with downstream topography.           

.. _fig-Perdigao:
.. figure:: ../_static/windconditions/Perdigao.jpeg
    :width: 600
    :align: center

    Phenomena of interest in the Perdigão experiment. `©American Meteorological Society <https://journals.ametsoc.org/doi/full/10.1175/BAMS-D-17-0227.1>`_. Used with permission. :cite:`fernando_perdigao_2019`

Besides *Perdigão*, the NEWA project produced a follow-up experiment in complex terrain at the *Alaiz* site :cite:`santos_alaiz_2020` to study the interaction between the *Tajonar* ridge, of similar height as *Perdigão* hills (~250 m), and the *Alaiz* mountain range (~700 m), both separated by a ~ 6-km wide valley. The high altitude of *Alaiz* results in larger interaction with the ABL structure and mesoscale flow. 

.. todo:: 
   * Perdigão benchmark.  
   * Alaiz diurnal cycles benchmark.


Benchmarks on Intended Use
--------------------------
This section describes benchmarks in the application space, where flow models are integrated with the statistics of the long-term wind climate to predict the quantities of interest that are relevant for the inteded uses of the model. Before running these benchmarks, flow models should have demonstrated their predictive capacity by validating as many flow cases as possible from the :ref:`benchmarks_phenomena` section. Now, the objective is to quantify the impact that this formal V&V process has on the applications of interest. 

The assessment shall be done on as many sites as possible to cover a wide range of operational conditions. This will require contribution from measurement campaigns from industry to complement the publicly available experimental campaigns.

.. _apps-wra:

Assessment of Wind Resource, Energy Yield and Site Suitability 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Cabauw :cite:`rodrigo_comparing_2018`.

   * NEWA Challenge

.. toctree::
   :glob:
   :maxdepth: 1

   benchmarks/mesomicrochallenge.rst

Numerical Site Calibration
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. todo:: 

   * Add Alaiz site calibration 


References
----------
.. bibliography:: windconditions_references.bib
   :all: