=======================
Interpreting AFNI's QC measures 
=======================

The following is a copy of the help.html file generated from afni_proc.py with the -html_review_style pythonic option. 
=======================

For a review of best practices and field standards for QC, see 'Reynolds, R. C., Taylor, P. A., & Glen, D. (2023). Quality control practices in fMRI analysis: philosophy, methods, and examples using AFNI. Frontiers in Neuroscience, 16. https://doi.org/10.3389/fnins.2022.1073800` <https://doi.org/10.3389/fnins.2022.1073800>`__.

OVERVIEW
-----------------------

QC organization
    The quality control (QC) is organized into thematic blocks to
    check, such as original data acquisition, different alignments,
    motion, regression modeling, and more. At the top of the QC page,
    there is a navigation bar with a label for each QC block (vorig,
    ve2a, etc.) that functions as a button to the top of that section.

Rating
    Beneath each section label is a(n initially empty) QC button,
    which users can click to set a rating for that QC block and for
    the overall subject rating ("FINAL"). Clicking on the QC button
    toggles its state through good (+), bad (X) or other (?, which may
    include 'ugly', or just a hint to revisit later).  Users can also
    use convenient 'filler buttons' at the right (A+, Ax, etc.), when
    the ratings are constant/uniform-- one hopes for 'all good'
    processing, but who knows...

Commenting
    Additionally, users can ctrl+click on the QC button to enter a
    comment for that block.  For example, they can write why a rating
    was good or bad, or what question led them to rate it as
    'other'.

Saving info
    If you have a local server running, then as you click and type
    the rating/QC buttons the information will be saved automatically
    in the QC directory.  The 'SAVE:' button in the upper-left corner
    shows whether the server is running: + if the letters are green and visible, then the server is running (and your QC     info is being saved). + if the letters are gray with a red line through them, then the
    server is not running (and your QC info is not being saved).
 
    It is useful to start the server and save QC/rating info for
    sharing and/or later using inclusion/exclusion criteria for the
    subject in group analysis.

    The ratings and comments are both saved in 'apqc_*.json'.
    The ratings are also saved in 'extra_info/out.ss_review.*.json', 
    which is a file that can be used as an input file to 
    gen_ss_review_table.py, combining the qualitative evaluations of
    the APQC HTML with the quantitative ones gathered by afni_proc.py, 
    for systematic evaluation and QC of subject data.


DEFINITIONS   
-----------------------

QC block 
    One thematic section of the QC form (original data, alignment
    step, etc.).  Each block has a label in the navigation bar (vorig,
    ve2a, etc.)-- click on the label to jump to that block. Click on 
    the button below the label to provide a rating for that block.

QC buttons
    Below each QC block label in the navigation bar is a button
    (initially empty after running afni_proc.py). The user can click
    on it to toggle its state to one of three ratings (good, +; bad,
    X; other, ?), as well as to enter a comment for that QC block (via
    ctrl+click).

'FINAL' 
    Label for the QC button to hold the user's overall/final
    evaluation of the subject's data and processing. (Clicking on this
    label does nothing.)

filler buttons
    |A+|, |Ax|, |A?|: these are located in the upper right corner of the
    navigation menu.  These can be used to provide uniform ratings
    across the QC buttons (click to fill empty buttons, double-click
    to fill *all* buttons, regardless of state).  
    |clr|-- double-clicking on this will empty all ratings+comments
    from the QC buttons.

'SAVING'
    Denoting whether the local server is running or not.  Python's Flask
    module is used to start a local server, so QC ratings and comments 
    can be saved as they are made.  
    This mode is ON when the SAVING button text is green and unobscured, 
    and it is OFF when the text is gray and covered by a red line.

'HELP'
    Button : well, how did you get here??

'BC', 'AC'
    When using the 'pythonic' HTML style, 1D-plotting (like motion
    enorm plots) also produces boxplots to summarize values.  When
    censoring has been applied, by default there will be two boxplots
    made: one of values 'before censoring' (BC), and one of values
    'after censoring' (AC).  Those labels are affixed in order to the
    titles of the boxplots.


SET BUTTON RATING   
-----------------------

To record an evaluation, click the button below any section label, and
toggle through: + : good, X : bad, ? : other (or 'revisit').

For speed, you can click 'filler button' |A+| once to fill all *empty*
buttons with +, or doubly to fill *all* buttons with +.  |Ax| behaves
the same for X, and |A?| for ?.

Double-click |clr| to clear all rating and comment values.

Pro-tip: if data are mostly all in a single state like good or bad,
just use filler buttons to save yourself click time, and then just
click any individual buttons that are different.  


COMMENT
-----------------------

Use ctrl+click (or cmd+click, on Macs) on a QC button to toggle a comment
window open/closed.

Save a comment with the green (left) button, or hit Enter at any point.
Remove a comment with the pink (right) button, or hit Esc at any point.

Any QC button with a comment gets a pair of quotes added, like ''+''.
Comments are independent of rating, but adding a comment to an empty
button changes its rating to ''?'' (which can be altered further from
there).

SAVE INFO
-----------------------

Have the local server running (check the 'SAVING' button in the 
upper-right corner).  

When the local server is running, the QC and rating information is saved
every time a button is updated.


KEYBOARD NAVIGATION
-----------------------

Use Tab to navigate the QC menu mirroring all above functionality.

Hit Tab to move through the menu.  Hit Enter on a section label to
scroll the page there.

On QC buttons hit Enter to toggle through the rating list.  Use
ctrl+Enter to open comments; as above, use Enter or Esc to keep or
erase, respectively.

On the filler buttons |A+|, |Ax| and |A?|, use Enter to fill empty
QC buttons and ctrl+Enter to fill *all* buttons. 
On |clr|, ctrl+Enter clears all rating and comment values.  

QC BLOCKS 
-----------------------

vorig
    Volumetric mages of data (EPI and anat) in original/native space.
    
ve2a
    Volumetric images of the alignment of the subject's anat
    (underlay/grayscale) and EPI (overlay/hot color edges) volumes. Likely
    these will be shown in the template space, if using the tlrc block.
    
va2t
    Volumetric images of the alignment of the standard space template
    (underlay/grayscale) and subject's anat (overlay/hot color edges)
    volumes.
    
vstat
    Volumetric images of statistics results (and, where available, effect
    estimates).  
    
    For task-based datasets (where stimulus timing was used in AP), the
    (full) F-stat of an overall regression model is shown.  Additionally,
    one can specify labels of stimuli or GLTs used in the afni_proc.py
    command, and statistical results will be shown.  For stimuli with
    effect estimates, the 'Coef' values will be displayed as the olay
    colors (preferably with the 'scale' block having been used in
    afni_proc.py, producing meaningful units of BOLD % signal change in
    the 'Coef' volumes).
    
    For resting-state and naturalistic scans, seed-based correlation maps are
    displayed (when the final space is recognized).
    
    Colorbar ranges and thresholds are chosen from either percentile
    values within the data set (preferably from within a WB mask,
    available when the 'mask' block was used in afni_proc.py) or from
    pre-set statistical levels (like p=0.001).  Each case is described.
    
mot
    Summary of motion and outlier information, which may each/both be
    used as censoring criteria.
    
    The 6 rigid body motion parameters (3 rotation + 3 translation) are
    combined into a single quantity: the Euclidean norm (enorm), which has
    approx. units of 'mm'.  Large changes in the enorm time series show
    moments of subject motion.
    
    Separate runs are shown with the background alternating between white
    and light gray.
    
    Boxplots summarize parameter values, both before censoring (BC) and
    after censoring (AC).
    
    And a grayplot of residuals (with motion/outliers/censoring) is
    provided.  The '-pvorder' is used for output, placing the time series
    in decreasing order of similarity to the top two principal components
    of the (masked) time series data.  The colorbar max is set to 3.29,
    the value at which a standard normal distribution N(0,1) has a
    two-sided tail probability of 0.001.  The grayplot's top row contains
    a plot of the motion enorm and outlier frac across time, for reference
    with the grayplot series.
    
mecho
    There are many ways to process multi-echo (ME) EPI data.  Fortunately,
    afni_proc.py provides the ability to include most of them in your FMRI
    processing.  Please see the afni_proc.py help for the full argument
    list of '-combine_method ..'.
    
    The OC/OC_A ('optimally combined') methods were proposed by Posse et
    al. (1999).
    
    When any of the 'tedana*' or 'OC_tedort' methods is chosen, then
    processing uses outputs from the Kundu et al. (2011) work.
    
    When any of the 'm_tedana*' methods is chosen, then processing uses
    outputs from the MEICA group's tedana tool.  For more details, see the
    TEDANA project webpage.
    
regr
    When processing with stimulus time series, both individual and
    combined stimulus plots are generated (with any censoring also shown).
    
    The degrees of freedom (DF) summary is also provided, so one can check
    if too many get used up during processing (careful with bandpassing!).
    
    The "corr_brain" plot shows correlation of each voxel with the errts
    average within the whole brain mask (what could be called the 'global
    signal').
    
    Two TSNR dsets can be shown.  In each case, voxelwise TSNR is shown
    throughout the full FOV, and any brain mask dset is just used for
    defining a region within which percentiles are calculated. The generic 
    formula for TSNR is: TSNR = average(signal) / stdev(noise).
    First, the TSNR of r01 after volreg is shown if the user used the '-volreg_compute_tsnr yes' opt in AP. Here, the        "signal" is the time series and the "noise" is the detrended time series.
    Second, the TSNR of the combined runs after regression modeling is
    shown. Here, the "signal" is the all_runs dset and the "noise" is the errts time series.
    
    When a mask is present, the olay's hot colors (yellow-orange-red) are
    defined by the 5-95%ile range of TSNR in the mask.  The 1-5%ile values
    within the mask are shown in light blue, and the lower values are
    shown in dark blue.  In the absence of a mask, then the colorbar goes
    from 0 to the 98%ile value within the whole dset.
    
radcor
    @radial_correlate plots (per run, per block). These can show
    scanner coil artifacts, as well as large subject motion; both factors
    can lead to large areas of very high correlation, which would be
    highlighted here.  
    
warns
    Several AFNI programs carry out consistency checks while
    processing (e.g., pre-steady state check, regression matrix corr
    warnings, left-right flip checks).  Warnings are conglomerated here.
    
    Each warning has one of the following levels: none undecided mild medium severe
    
    The warning level is written, with color coding, at the top of each
    warning's text box.  The QC block label 'warns' at the top of the page
    is also colored according to the maximum warning level present.  
    
qsumm
    This is the output of @ss_review_basic, which contains a loooot of
    useful information about your single subject processing.

