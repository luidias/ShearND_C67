# Noninjurious C6C7 Shear Data
This repository contains processed data used in the analysis of the biomechanical response of thirty-nine human Functional Spinal Units (FSUs) at the C6/C7 level when subjeceted to  pure shear loading. This data is provided here in full to facilitate FE model validation efforts.

## Load-displacement data
This directory contains sub-directories for each specimen (H1, H2, etc.), which in turn contain .csv files for individual tests on the given specimen. There are six files per specimen, one for each test condition (Anterior/posterior directions and 1, 10, and 100 mm/s). Test condition is reflected in the file name.

These files contain the 3D displacements, rotations, and loads that were experienced by the FSU under the respective test condition. The X, Y, and Z axes were aligned with the anatomical axes:
- X axis: Anteroposterior axis, with anterior as the positive direction. Shear loads were applied along this axis.
- Y axis: Craniocaudal (superior-inferior) axis. Cranial (superior) is positive.
- Z axis: Lateral axis. Right is positive.
  
Rotations around each axis follow the right hand rule: with the axis pointing out of the page, positive rotations are counter-clockwise.

The .csv files are laid out such that:
- Columns 1-3 are the X, Y, Z displacements of the superior vertebra relative to the inferior, measured im mm.
- Columns 4-6 are the X, Y, Z rotations of the same, measured in degrees.
- Columns 7-9 are the X, Y, Z loads generated during the test.

## Specimen Info.csv

This file contains demographic and anthropometric data for each specimen.
- **ID**: Identifier code for the specimen. Matches corresponding sub-directory in Load-displacement data directory.
- **Level**: FSU level. For this dataset, all specimens were at the C6/C7 level.
- **CT_Scanned**: Boolean representing whether CT scans were taken of the specimen.
- **ND_Test_Date**: Date when testing occured, in MM/DD/YYYY format.
- **Specimen_Mass_kg**: Mass of the specimen, in kg, including PMMA potting, reinforcements, and specimen mounting plates
- **Balancing_Mass_kg**: Counterbalance mass used for the test, in kg, made up of half of the total specimen mass and the mass of the superior fixturing hardware.
- **Age**: Age of donor, in years.
- **Sex**: Biological sex of donor.
- **Race**: Race of donor.
- **Weight_kg**: Weight of donor at time of death, in kg.
- **Height_cm**: Height of donor at time of death, in cm.
- **Cause_of_death**: Donor cause of death.
- **sup_endplate_ap_width_from_lat_view_mm**: AP width of superior endplate proximal to the C6/C7 intervertebral disc, in mm. Measurements were taken from lateral X-ray images.
- **inf_endplate_ap_width_from_lat_view_mm**: Same as above, for the inferior endplate proximal to the disc.
- **avg_ap_width_from_lat_view_mm**: Average AP width of both proximal endplates.
- **avg_fsu_vertebral_body_volume_mm3**: averaged volume of the cancellous bone of both vertebral bodies, in mm<sup>3</sup>.
- **avg_vert_body_treb_bv_fraction**: Average bone volume fraction (BV/TV) of the cancellous bone in both vertebral bodies, as a ratio of bone volume to total volume.
- **Disc_Degen_Score**: Disc degeneration score, per the method established by Walraevens et al. [1], graded using CT scans. This is the sum of scores given to the disc for height loss, osteophytes, and endplate sclerosis. Possible scores are 0-9, where higher scores represent more degenerated discs.
- **Disc_Degen_Grade**: Disc degeneration grades correponding to the score. Possible values are None, Mild, Moderate, or Severe.
- **DD_Height_Loss**: Disc Height loss score. Possible scores of 0-4.
- **DD_Ant_OP**: Score for presence of anterior osteophytes, based on osteophyte size. Possible scores of 0-3.
- **DD_Endplate_Sclerosis**: Score for presence of proximal endplate sclerosis, based on severity. Possible scores of 0-2.
- **FJ_Degen_Score**: Facet Joint degeneration score, per Walraevens et al. [1], graded using CT scans. This is the sum of scores given for hypertrophy, osteophytes, articular irregularities, and joint space narrowing. Possible scores are 0-5, where higher scores represent more degenerated facet joints.
- **FJ_Degen_Grade**: Facet Joint degeneration grades correponding to the score. Possible values are None, Mild, Moderate, or Severe.
- **FJD_Hypertrophy**: Score for presence of hypertrophy. Possible scores are 0-2.
- **FJD_Osteophytes**: Score for presence of osteophytes. Possible scores are 0 or 1.
- **FJD_Surface_Irregularity**: Score for irregularity of articular surfaces. Possible scores are 0 or 1.
- **FJD_Joint_Narrowing**: Score for joint space narrowing. Possible scores are 0 or 1.

## Test Info.csv

This file contains information on specific tests carried out on the specimens. Each row entry represents one test. Specimen-specific data is repeated from Specimen Info.csv. Test-specific data is described below:
- **direction**: direction in which shear loads were applied (anterior or posterior).
- **disp_rate_mm_s**: displacement rate at which the test was carried out, in mm/s.
- **stiffness_1**: The Phase I Stiffness, in N/mm, calculated from the slope of the load-displacement data using a breakpoint analysis.
- **stiffness_2**: The Phase II Stiffness, in N/mm, calculated from the slope of the load-displacement data using a breakpoint analysis.
- **intercept_1**: Y-intercept of the linear regression from which Phase I stiffness was taken.
- **intercept_2**: Y-intercept of the linear regression from which Phase II stiffness was taken.
- **breakpoint_mm**: Location of breakpoint between the Phase I and Phase II response, on the displacement axis.
- **Calculated R2_1**: Goodness of fit (R<sup>2</sup>) for the Phase I regression line.
- **Calculated R2_2**: Goodness of fit (R<sup>2</sup>) for the Phase II regression line.
- **Calculated R2_3**: Goodness of fit (R<sup>2</sup>) for both regression lines in the breakpoint analysis.
- **peakLoad_N**: Maximum shear load during the test, in N.
- **peakDisp_mm**: maximum displacement during the test, in mm.


## References
[1] Walraevens J, Liu B, Meersschaert J, Demaerel P, Delye H, Depreitere B, et al. Qualitative and quantitative assessment of degeneration of cervical intervertebral discs and facet joints. Eur Spine J Off Publ Eur Spine Soc Eur Spinal Deform Soc Eur Sect Cerv Spine Res Soc. 2009 Mar;18(3):358–69
