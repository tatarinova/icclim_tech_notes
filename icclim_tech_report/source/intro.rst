
Intro
======

ICCLIM is short of Indice Calculation CLIMate, a Python library provided routines for climate indices calculation.

Actually, ICCLIM computes 49 climate indices defined by European Climate Assessment & Dataset(ECA&D) based on temperature and precipitation variables:

	- 11 cold indices (GD4, CFD, FD, HD17, ID, CSDI, TG10p, TN10p, TX10p, TXn, TNn)
	- 1 draught indice (CDD)
	- 9 heat indices (SU, TR, WSDI, TG90p, TN90p, TX90p, TXx, TNx, CSU)
	- 14 rain indices (RR, RR1, SDII, CWD, R10mm, R20mm, RX1day, RX5day, R75p, R75pTOT, R95p, R95pTOT, R99p, R99pTOT)
	- 4 snow indices (SD, SD1, SD5cm, SD50cm)
	- 6 temperature indices (TG, TN, TX, DTR, ETR, vDTR)
	- 4 compound indices (CD, CW, WD, WW)
	
Detailed description of each indice is available at http://eca.knmi.nl/documents/atbd.pdf.

Initialy ICCLIM was designed for online climate indices computing on the climate4impact portal(LINK). 
In spite of existence of other packages able to compute climate indices (`CDO <https://code.zmaw.de/projects/cdo>`_, `R package <http://etccdi.pacificclimate.org/software.shtml>`_ ),
it was decided to develop a new software in Python.
Python language was first of all choosen to interface with `PyWPS <http://pywps.wald.intevation.org/>`_: Python implementation of Web Proccessing Service
(WPS) Standard.
Another reason was to interface eventially with the `OpenClimateGIS <https://earthsystemcog.org/projects/openclimategis/>`_.

The documentation is available at `<http://icclim.readthedocs.org>`_.

The developer repository is found here: `<https://github.com/tatarinova/icclim>`_


