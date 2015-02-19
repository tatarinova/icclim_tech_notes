
Temporal aggregation
===============================

Each indice can be calculated as annual, winter half-year, summer half-year, winter, spring, summer, autumn and monthly values.
The get_dict_temporal_slices() function from time_subset.py allows to extract data slices depending on selected temporal aggregation.
The output is a dictionary with keys as (temporal_aggregation_mode, year) and values are grouped in a tuple with 4 elements: (dt_centroid, dt_bounds, dt_arr, values_arr).
Bellow is an example with the "JJA" season temporal aggregation:

.. figure:: /images/temp_aggregation.png
   :scale: 50%
   
In the following, looping on keys, corresponding values_arr is passed to indices computing routines (**calc_indice.py** and **calc_indice_perc.py**).
All centroid time steps are groupped then in a time steps vector to be written in output netCDF file as values of "time" variable.
The time bounds in turn are groupped in time bounds array to be written in output netCDF file as values of "time_bounds" variable.

