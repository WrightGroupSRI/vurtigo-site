---
title: "Release 3.2.0 Notes"
draft: true
image: "null.png"
weight: 8
---
## New Features
- Configurable catheter tip can now be defined by two tracked locations and a tip offset
- Catheter xml movie recording
- Isosurface generation from volumes
- "Rotational Tracking" mode to follow a catheter with a plane along its tip
- Optional depth-peeling setting
- Import manager with support for vtk surfaces (.vtp/.vtk) and external volume formats (NIFTI, MetaImage, SLC, and NRRD)
- MetaImage exporter for volumes
- "Thresholded Tracking" mode to follow a catheter once it has moved a minimum distance
- Plugin update rate now reported in frame rate label
- Volume scrolling modifiers to allow different scroll step distances
- A Matrix Object has been added to Vurtigo
- An option has been added to invert a volume's intensity values
- Minimum intensity projection and additive blend modes have been added to the volume raycasting options
## Improvements
- Contours can now be saved
- Improved transparency handling for planes
- Catheter data recordings can now include timestamps
- Displaying user-friendly object type names
- Most settings now consolidated into a single dialog
- Improved point set editing performance
- Catheter display properties can now be saved as a preference
- Improved performance of catheter display and recording
- Volume crop box now applies to planes and isosurfaces, and can be reset
- Improved performance for in-procedure mesh painting
- Expanded DICOM support for different modalities and vendors
- Handling image volumes with negative intensity values
- Improved volume raycasting of greyscale images loaded through the image stack loader
- Image stack loader workflow improvements: warns user if volume does not contain enough slices, allows cancelling
- Landmark registration now creates new point and slice objects instead of editing the source objects
## Bug Fixes
- Hang when editing piecewise function
- Crash when attempting to volume-render a slice
- Catheter History does not save physiology data
- Crash when deleting a plane that is being tracked by the CathTracking plugin
- Crashes and freezes when changing information in the GeomServer plugin while it is connected
- Permanent objects deletable in object browser
- Objects can be overwritten or fail to save into a scene
- Match Triggers option crashes on some volumes
- Segmentation fault when cancelling a Save Object operation
- Frame rate inaccurate
- Conflicts and duplicate handling of user interaction with camera and objects
- Minimum plugin update interval is incorrect
- Race condition in object manager can cause deadlock
- Synchronized scrolling planes can cause a volume plane to disappear
- Using the Mask or Mesh tool deselects all 3D windows
- Registration fails when the source object is a polydata
- Maximum window size in window/level dialog is off by one
- Cancelling an EP mesh color change results in a black mesh
- Color transfer function issues: attempting to use a newly created ctf results in garbage, duplicate signal-slot connections result when editing a ctf in use, values are not set correctly when using setColorFunction
- Landmark registration does not work correctly for slice objects
## Known Limitations
- Using the Camera interpolation plugin to "Wobble" the view while the geometry server is connected can cause a crash
- Volume meta-information is not saved to the vurtigo object format
- Not all DICOM files are supported
- The transformation matrix for external volume formats, if one exists, is ignored
- "Checkerboard" stereo rendering crashes on some systems
- EP Mesh "Show EP Data" option does not work
- 3D Point object table does not update automatically when the object changes
