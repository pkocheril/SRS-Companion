# SRS Companion App
Companion application for quick frequency/wavelength and time delay conversions, simple image processing, and exporting. Continuously a work-in-progress. No guarantees of accuracy, completeness, or functionality.

Written in HTML.


## Highlights and main functions
* Fast and lightweight
* No installation required (runs in a web browser, even offline)
* Automatic preparation of input files for hyperspectral sweeps
* Built-in power correction and rough spectral analysis for hyperspectral sweeps


## Usage
Simply double-click the ```.html``` file and the app will launch in your default web browser.


### Basic conversions
The top two panes are used for OPO wavelength and time delay calculations, intended for use with a picoEmerald (Stokes wavelength at 1031.2 nm, configurable; pump wavelength tunable from the output of a NIR OPO). A calibration curve (with input reference wavelength & time and a corresponding slope) is used to calculate the time delay for the desired wavelength.

### Sweep file generation
The powershell script and list of time delay positions required for automated sweeping can be generated automatically with this companion app.

A handful of preset sweep conditions are preloaded (CD, CH, amide I), but the start and end wavelengths and step size can also be configured manually. You should also specify the working directory (where you plan to place the ```Tstep.txt``` file).

Once the inputs are set, the "Generate" button will show a preview of the input conditions. The "Export" buttons will then download the powershell script and list of delay positions to the ***Downloads*** folder (or wherever the browser is configured to save).

### Power correction
After a sweep, the output ```.tif``` stack and recorded ```Sweep_parameters.txt``` can be inputted for per-frame power correction. The scrubber below the image allows you to view the stack to ensure that the frames loaded properly.

After applying the power correction, you should see two copies of the same stack, showing the data before and after power correction. The appearance in this view is unchanged, since the correction is applied per-frame, but by ***drawing a box on the original (left-side) image***, a spectrum visualizing that region-of-interest (ROI) will appear for both the original and power-corrected stacks.

Once satisfied, press the "Export corrected stack" button to save a new .tif with the power-corrected values into the ***Downloads*** folder.

### Spectral analysis
If desired, after power correction, the corrected stack can be used to plot spectral profiles in desired regions and compare them.

The envisioned use-case is selecting a region of interest on the left iamge (e.g., on a cell) and a region of background on the right image (e.g., the surrounding buffer). The spectral profiles of the two drawn regions are then plotted, along with the subtraction of the two.

The spectra can then be exported as a single ```.csv``` after processing.

# How to cite
If you found any of these functions useful, please cite this code as:

1. PA Kocheril, RE Leighton, N Naji, D Lee, H Wang, J Du, and L Wei*. Towards accurate predictions of bond-selective fluorescence spectra. DOI: 10.48550/arXiv.2601.11902
