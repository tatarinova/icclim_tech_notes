
Files tree
===============================

.. code-block:: sh

    - icclim/
        - LICENCE
        - NOTICE
        - MANIFEST.in
        - README.md
        - setup.py
        - .git/         - hidden
        - .gitignore    - hidden
        - ECA_indices_description.txt                   (link to the ECA&D indices documentation)
        - ICCLIM_files_tree.txt                         (files tree)
        
        - icclim/
            - __init__.py
    
            - libC.c                                    (routines written in C)
            
            - time_subset.py                            (function for temporal aggregation)      
            - icclim.py                                 (the principal module containing the principal function for indice computing)        
            - percentile_dict.py                        (function for percentiles computing)        
            - calc_indice.py                            (elementary routines for indices computing)                        
            - calc_indice_perc.py                       (elementary routines for percentile-based indices computing)
            - set_globattr.py                           (functions for setting global attributes in output netCDF file)
            - set_longname_units.py                     (functions for setting "longname" and "units" attributes of indice variable in output netCDF file)
            - set_longname_units_custom_indices.py      (functions for setting "longname" and "units" attributes of custom indice variable in output netCDF file, actually for the indices SU, CSU and TR with user selected threshold)
            
            - util/
                - __init__.py
                
                - util_nc.py                            (functions manupilating ...)
                - util_dt.py                            (functions manipulating time steps vector)
                - files_order.py                        (functions to make input files list in correct order)
                - callback.py                           (default callback functions useful for progress bar printiong)
                - arr_size.py                           
                - OCGIS_tile.py                         (useful for spatial chunking)            
                - spatial_stat.py                       (spatial statistics)
                - anomalies.py                          (anomalies computing)
                - regrid.py                             (functions for simple regridding, rectangular "lat/lon" grid)
                
            - icclim_doc/                               (documentation)
                - source/
                    - images/                           (folder to store images used in the documentation)
                    - _static/                          (?)
                    
                    - conf.py
                    - index.rst
                    - intro.rst
                    - important_to_know.rst
                    - installation.rst
                    - python_api.rst
                    - output_metadata.rst
                    - contacts.rst
                    - icclim_ocgis.rst                            
                - build/
                    - doctrees/                         (?)
                    - html/                             (built HTML files)                
                - Makefile
            
    
            - script_examples/
        
