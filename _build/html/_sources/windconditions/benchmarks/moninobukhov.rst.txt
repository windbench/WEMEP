Monin Obukhov Similarity Theory (MOST)
======================================

Background
~~~~~~~~~~
Monin Obukhov (M-O) similarity theory (Monin and Obukhov, 1954) sets the point of departure of modern micrometeorology (Foken, 2006). It is valid in the surface layer, i.e. approximately in the first 10% of the ABL, where Coriolis effects are negligible compared to friction, and under stationary and horizontally homogeneous conditions with no radiation. In these ideal conditions the vertical variations of wind direction, shear stress, heat and moisture fluxes are constant. M-O theory states that any dimensionless turbulence characteristic will only depend on a reduced set of scales. In addition to friction velocity (u*) and the height above the ground (z), as basic scales in neutral conditions, the surface (virtual) potential temperature Θ0 and kinematic heat flux (wΘ) are also required in thermally stratified conditions. The Obukhov length scale L is made of a combination of these parameters,

[L equation] 

where g is the gravity and κ is the von Karman constant. A dimensionless height z/L is used as stability parameter (z/L < 0 for unstable, z/L > 0 for stable and z/L = 0 for neutral conditions). Any dimensionless turbulent characteristic will depend solely on this parameter. By integration of the velocity and potential temperature gradients, well-known logarithmic profiles are obtained:

[lag-laws]

where U is the mean velocity at height z, z0 and z0t are the roughness length for momentum and heat, Θ* is a temperature scale,Θ is the mean (virtual) potential temperature at height z, Cμ is a constant, and Φx and Ψx are stability functions obtained from flux-profile experiments in flat terrain (see for instance, Panofsky and Dutton, 1984). k is the turbulent kinetic energy and ε is the turbulent dissipation rate, also a function of the stability parameter.

M-O theory is used to design wind engineering surface layer models. When an empty domain is simulated in steady-state with homogeneous surface conditions the flow should produce the fully-developed log-profiles predicted by the theory. These are the conditions that will be simulated in this test case.

For instance, Richards and Hoxey (1983) calibrated the RANS k-ε turbulence model by enforcing consistency with M-O theory in the surface layer in neutral conditions. Alinot and Masson (2005) followed the same approach to derive consistency conditions for a k- ε model in stratified conditions.

Scope and Objectives
~~~~~~~~~~~~~~~~~~~~~~~~
This test case should be mandatory for anyone using surface layer models since it describes the fundamental physics in flat terrain conditions. Simulations of homogeneous profiles in an empty domain also allow to check the equilibrium of the wall functions with the turbulent flow model (Blocken et al., 2007). In a building-block approach, it shall be used as a precursor validation to any other benchmark.

References 
~~~~~~~~~~

Alinot C., Masson C., 2005, k-ε Model for the Atmospheric Boundary Layer Under Various Thermal Stratifications, Transactions of the ASME 127: 438-443

Blocken B., Stathopoulos T., Carmeliet J., 2007, CFD simulation of the atmospheric boundary layer – wall function problems, Atmospheric Environment 41(2):238-252

Monin A.S., Obukhov A.M., 1954, Basic Laws of Turbulent Mixing in the Atmospheric Surface Layer, Trudy Geofiz. Inst. Acad. Sci. U.S.S.R. 24(151):163-187

Foken T., 2006, 50 Years of the Monin-Obukhov Similarity Theory, Boundary-Layer Meteorol. 119:431-447

Richards P.J., Hoxey R., 1993, Appropriate boundary conditions for computational wind engineering models using the k–ε turbulence model, J. Wind Eng. Ind. Aerodyn. 46-47: 145–153

Panofsky H.A., Dutton J.A., 1984, Atmospheric Turbulence, Models and Methods for Engineering Applications, John Wiley & Sons.

