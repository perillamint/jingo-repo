# What is it?
Undertale gameplay automator.

# Architecture
## Screen capture
* Grab screen and convert it to OpenCV matrix.
* Pass OpenCV matrix and timestamp to CV module. 
* Use X11 or Wayland to capture screenshot of Undertale.

## Computer Vision
* Process captured image and timestamp to produce key sequence.
* Pass key sequence and timing to output module.

## Output
* Emulate keypress.
* Use X11 or Wayland API to emulate keypress.

## Driver
* Routes data between modules.
* Initialize each modules.
* Set CV module mode.