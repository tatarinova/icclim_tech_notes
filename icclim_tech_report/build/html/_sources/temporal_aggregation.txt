
Temporal aggregation
===============================

Each indice can be calculated at annual, winter half-year, summer half-year, winter, spring, summer, autumn and monthly frequency.
The get_dict_temporal_slices() function from time_subset.py allows data extraction into slices depending on selected temporal aggregation.
The output is a dictionary with keys as (temporal_aggregation_mode, year) and values as a tuple with 4 elements: (dt_centroid, dt_bounds, dt_arr, values_arr).
Bellow is an example for the "JJA" season temporal aggregation:

.. figure:: /images/temp_aggregation.png
   :scale: 90%
   
In the following, looping on keys, corresponding values_arr is passed to indices computing routines (**calc_indice.py** and **calc_indice_perc.py**).
All centroid time steps are groupped then into time steps vector to be written in output netCDF file as values of "time" variable.
The time bounds are also groupped in 2D array to define values of "time_bounds" variable.

