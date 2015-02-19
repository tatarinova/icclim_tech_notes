.. _icclim_ocgis:

Python optimization with C
==================================

Intro
~~~~~~

`<http://kortis.to/radix/python_ext/>`_

ICCLIM modules **calc_indice.py** and **calc_indice_perc.py** contain basic routines for manipulating 3D arrays.


There are 2 approaches to process 3D arrays:

    - Using existing routines from the `NumPy <http://docs.scipy.org/doc/numpy/reference/>`_ library (min/max/... along time dimension gives 2D ouput array).
    
        For example, to compute the indice TXn (*minimum value of daily maximum temperature*):
            
            >>> TXn = tasmax_array.min(axis=0)
            
    - Creating new routines for computing, as for example *maximum number of consecutive days where maximum temperature > 25 degrees Celsius* (CSU) given below.
        
        .. code-block:: sh
        
            Pseudocode:
                
                input: 3D tasmax_array (A 3D array is a "cube" with depth as time dimension.)
                output: 2D CSU_array            
                
                we reserve memory for CSU output array
                
                for i in lines:
                    for j in columns:
                        we compute CSU for the current pixel [i,j] of tasmax_array along axis time
                        we write the result to the pixel [i,j] of the CSU_array
          
        It should be noted here that use of nested loops in Python decrease significantly its performance. Thus, for that purpose it is recommended to create routines in C that can be called in Python.



How to call C from Python
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: In ICCLIM, all C routins are stored in **libC.c**.

1. Write a C function you want to use in the libC.c.
2. Compile libC.c:

    .. code-block:: sh
    
        $ gcc -fPIC -g -c -Wall libC.c
    
3. Create a shared object (.so file):

    .. code-block:: sh
    
        $ gcc -shared -o libC.so libC.o
    
4. In a Python program where you want to call C (if both files are in the same directory):

    .. code-block:: py
    
        import ctypes
        from numpy.ctypeslib import ndpointer
        import os
    
        my_rep = os.path.dirname(os.path.abspath(__file__)) + os.sep
    
        libraryC = ctypes.cdll.LoadLibrary(my_rep+'libC.so')
            
        my_function = libraryC.my_function_from_LibC
    
        my_function.argtypes = [ <list of ctypes argument types in the same order as in my_function_from_LibC> ] 
        
        my_function( <corrsponding arguments separated by a comma> )
   



.. note:: Ctypes documentation: `<https://docs.python.org/2/library/ctypes.html>`_
.. note:: Corresponding ctypes types: int ---> ctypes.c_int; double* ---> ndpointer(ctypes.c_double); etc
.. note:: See examples in **calc_indice.py** and **calc_indice_perc.py**.
 

