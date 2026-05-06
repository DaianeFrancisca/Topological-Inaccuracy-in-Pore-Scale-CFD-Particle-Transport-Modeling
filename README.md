# Topological-Inaccuracy-in-Pore-Scale-CFD-Particle-Transport-Modeling

Image Resampling and Interpolation Protocol for Pore-Scale Modeling
This repository contains the image processing workflow used in the study "Resampling Factor and Interpolation-Driven Solid Phase Dilation as Drivers of Topological Inaccuracy in Pore-Scale CFD Particle Transport Modeling".
The goal of this protocol is to assess how different Resampling Factors (RF) and Interpolation Methods affect the geometric and topological integrity of porous media samples (S1–S7).

# 1. Purpose of the Code/Workflow 

The primary purpose of this workflow is to quantify the "Solid Phase Dilation" effect. By reducing the resolution of X-ray Computed Tomography (μCT) images, we evaluate the limits of physical representativeness for Computational Fluid Dynamics (CFD).
Rescaling Range: RF 0.5 down to RF 0.1 (10% of original resolution).
Interpolation Methods Tested: * Nearest Neighbor (NN)
Bilinear/Trilinear
Bicubic/Tricubic

# 2. ImageJ Setup & Requirements
Software: ImageJ (v1.53 or higher) or FIJI (https://imagej.net/ij/). 
Plugin: No external plugins are required; the study utilizes native ImageJ "Scale" functions.
Data: 8-bit or 16-bit TIFF stacks representing the pore space.

# 3. How to Use 
## Rescaling the samples
Load the Image stacks: Open your original 3D stack in ImageJ (File > Open).
Access Scaling Tool: Go to Image > Scale...
Configure Parameters:
X, Y, and Z Scales: Enter the desired Resampling Factor (e.g., 0.5 for 50% or 0.1 for 10%).
Interpolation: Select between None (Nearest Neighbor), Bilinear, or Bicubic.
Process: Ensure "Average when downsizing" is unchecked to strictly test the interpolation algorithms as described in the paper.
Save: Export the resulting stack as a .tiff for topological analysis (e.g., using BoneJ or Pore-Network Modeling).

## Checking the area, porosity, histograms...
Set the measurements that you want to see: go to Analyze > Set Measurements and select the parameters that is relevant for you (In this research it was selected the fields of Area, Standart Deviation, Area Fraction, mean gray volume and the Display label was also activated)
Select your samples (the softare allow generate one spreadsheet with all the samples datas)
Get the measurements datas: Go to Analyse > Measure (or press Ctrl + M)
Save datas: You can export the spreadsheet or copie the datas
Get the porosity: After this process you will get the solid area percentage, so in order to get the porosity just subtract this value from 100%

# 4. How to Run the Tests 
## Checking the Interpolatios' Influence
To replicate the accuracy tests shown in the manuscript (specifically for RF 0.5):
Baseline: Keep the original image at RF 1.0.
Execution: Run the scaling process three times on the original stack using RF 0.5 (please, note that the softare firstly apply only to x and y axes, resulting in a bilinear transformation. So you have to adjust manually  to the z-axis), selecting a different interpolation method (Nearest Neighbor, trilinear, and tricubic) each time.
Comparison: * Measure the Mean Pore Diameter and Connected Porosity.
Compare the resampled results against the RF 1.0 baseline.
Threshold Check: Verify if the pore throats remain above the 3-voxel threshold. If a throat is reduced below 3 voxels, numerical occlusion (hydraulic collapse) is expected.
When correctly executed, your ImageJ interface and resulting data should align with the sensitivity analysis illustrated below:
(Reference: Figure 6 from Silva et al., 2026, Comparative analysis of interpolation methods (Tricubic, Trilinear, and Nearest Neighbor) on the digital representation of granular media. (a) Normalized Porosity (P/P0) shows a decay of measured porosity across different interpolation schemes. (b) Porosity Loss (%) shows the percentage reduction of the pore phase for each sample under the tested algorithms. (c) Relative Error (%): comparison of measurement deviation, with dashed lines indicating 5% and 10% tolerance thresholds. (d) Multi-criteria Performance Profile is the radar plot aggregating Pearson r, R2, Bias Score, Consistency, and Accuracy metrics, illustrating the overall superiority of the Nearest Neighbor or specific interpolation approach in maintaining the original geometric properties..)

## Checking the Rescaling' Influence
To replicate the accuracy tests shown in the manuscript (specifically for trilinear interpolation):
Baseline: Keep the original image at RF 1.0.
Execution: Run the scaling process on the original stack using RF 0.5, 0.33, 0.25, 0.2, 0.17, 0.17, 0.125, 0.11 and 0.1, selecting a different interpolation method trilinear each time (please, note that the softare firstly apply only to x and y axes, resulting in a bilinear transformation. So you have to adjust manually  to the z-axis).
Comparison: * Measure the Mean Pore Diameter and Connected Porosity.
Compare the resampled results against the RF 1.0 baseline.
Threshold Check: Verify if the pore throats remain above the 3-voxel threshold. If a throat is reduced below 3 voxels, numerical occlusion (hydraulic collapse) is expected.
Example Output
When correctly executed, your ImageJ interface and resulting data should align with the sensitivity analysis illustrated below:
(Reference: Figure 4 from Silva et al., 2026, Systematic downsampling analysis for the seven granular media specimens. Panels (a) through (g) correspond 
to Samples 1 to 7, respectively. Within each panel, the Resampling Factor (RF) increases from 1 to 10, corresponding 
to a reduction in the Rescale Factor from 1.0 to 0.1. This figure illustrates the differential impact of resolution reduction 
on coarse-grained vs. fine-grained samples, highlighting the increased vulnerability of finer textures (e.g., Sample 7) 
to digital information loss at low RF.)

# 5. Contact
For questions regarding the methodology or data, please contact: Daiane Francisca do Nascimento Silva
Email: daiane.francisca@ufpe.br 
