Chunking
============






In case if requested datasets exceed OPeNDAP/THREDDS transfer limit, ICCLIM applies chunking method to transfer and process.
Chunksize is dynamicly adapted to the data maximum transfer size. Data cutting is realized along the time dimension (spatial chunking):

.. figure:: /images/chunking_1.png
   :scale: 90%
   
The figure bellow shows how ICCLIM estimates an optimal tile dimention:

.. figure:: /images/chunking_2.png
   :scale: 90%
   
*OCGIS_tile.py* provides a function which returns the start and end indices vertically and horizontally for each chunk:

.. figure:: /images/chunking_3.png
   :scale: 90%
   
The transfer and processing chunks will be in the following order:

chunk 1 = array[:, 0:50, 0:50]

chunk 2 = array[:, 0:50, 50:100]

chunk 3 = array[:, 0:50, 100:150]

chunk 4 = array[:, 50:100, 0:50]

chunk 5 = array[:, 50:100, 50:100]

chunk 6 = array[:, 50:100, 100:150]

chunk 7 = array[:, 100:120, 0:50]

chunk 8 = array[:, 100:120, 50:100]

chunk 9 = array[:, 100:120, 100:150]

.. note::  The second bound in Python is excluded.
