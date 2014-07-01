LOFAR Ionosphere Scripts for Peeling, Applying, and Imaging
===========================================================

Authors:
* David Rafferty
* Bas van der Tol

These scripts allow for semi-automated derivation and application of ionospheric
TEC screens for LOFAR data. The following scripts are available:
* __ion_peel.py__: Performs peeling to derive direction-dependent phase solutions
* __ion_apply.py__: Applies the TEC screens derived by the TECSCREEN operation in LoSoTo
* __ion_image.py__: Images, with and (optionally) without the TEC screen

Peeling (ion_peel.py)
---------------------
The ion_peel.py script takes as input a set of measurement sets at various frequencies and
(possibly) multiple fields and performs directional calibration that can be
used to correct for time- and position-dependent ionospheric effects. All
solutions are copied to a single H5parm file that can be used with LoSoTo to
fit for TEC values and to derive phase screens that may be used to make
ionospheric corrections with the AWimager.

Command-line arguments define the position and radius over which to search for
potential calibrators, the minimum apparent flux for a calibrator, the maximum
size of a calibrator, etc. From these inputs, the script can determine the
optimal set of calibrators to solve for in each band and in each field.  At a
given frequency, only the field in which the calibrator is brightest is used.

All the measurement sets are assumed to be a single directory (defined by the
'indir' option). All results are saved in an output directory (defined by the
'outdir' option).

For more information on the options, run:

    ion_peeling.py --help


TEC Screen Application (ion_apply.py)
-------------------------------------
The ion_apply.py script takes as input a H5parm file with a TEC screen fit generated
by the TECSCREEN operation in LoSoTo. By default, the screen is exported to all
measurement sets in the specified input directory (default is '.').

For more information on the options, run:

    ion_apply.py --help


Imaging (ion_image.py)
----------------------
The ion_image.py script automates the imaging of a dataset, including the
application of a TEC screen. By default, all measurement sets in the specified
input directory are concatenated and imaging together.

For more information on the options, run:

    ion_image.py --help

