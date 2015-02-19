.. _icclim_ocgis:

Python optimization with C
==================================

`<http://kortis.to/radix/python_ext/>`_

ICCLIM modules **calc_indice.py** and **calc_indice_perc.py** contains elementary routines manipulating 3D array.


To process 3D arrays:

    - We use existing routines of `NumPy <http://docs.scipy.org/doc/numpy/reference/>`_ library (compute min/max/... along time axis, i.e. for each pixel => we have then 2D array in output).
        Example: indice TXn (Minimum value of daily max temperature).
            
            >>> TXn = tasmax_array.min(axis=0)
            
    - We code ourselves.
        Example: indice CSU (Maximum number of consecutive days where max temperature > 25 degrees Celsius).
        
        .. code-block:: sh
        
            Pseudocode:
                
                input: 3D tasmax_array (A 3D array is a "cube" with depth as time axis.)
                output: 2D CSU_array            
                
                we reserve memory for CSU output array
                
                for i in lines:
                    for j in columns:
                        we compute CSU for the current pixel [i,j] of tasmax_array along axis time
                        we write the result to the pixel [i,j] of the CSU_array
          
        Implementation of that in Python is not prefered: it is not performant in case of nested loops.
        It is better to implement nested loops routines in C, and then call them from Python program.



How to call C from Python
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: In ICCLIM all C routins are stored in **libC.c**.

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
    
        my_function.argtypes = [list of ctypes argument types in the same order as in my_function_from_LibC] 
        
        my_function(corrsponding arguments separated by a comma)
   



.. note:: Ctypes documentation: `https://docs.python.org/2/library/ctypes.html>`_
.. note:: Corresponding ctypes types: int ---> ctypes.c_int; double* ---> ndpointer(ctypes.c_double); etc
.. note:: See examples in **calc_indice.py** and **calc_indice_perc.py** files.
 

