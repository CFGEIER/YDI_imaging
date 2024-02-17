=======================
AFNI processing
=======================

Preprocessing at the individual subject level
=======================

Overview of Steps:
1. Download files from BIRC (see Data_Transfer link). 
2. Run 'dcm2niix' to reconstruct 2D images (dicom files) into 3D and 3D+time. 
3. Transfer the *.nii and *.json files for the anatomical images (T1) and the functional images (T2*) to specific file locations on GACRC
4. Run the @SSwarper program to skull-strip and then non-linearly warp and transform the participant's anatomical image to standardized space (Haskins Pediatric Template). 
5. Modify the afni_proc.py script, updating the subject # and the task. 
6. Run afni_proc.py. This will perform standard preprocessing steps (e.g., slice timing correction, motion estimation, etc.) and run an individual-level GLM (using the program 3dDeconvolve). 
7. Evaluate output using QC steps outlined on this site. 


