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

# 3. How to Use (Step-by-Step)
## Reascaling the samples
Load the Image stacks: Open your original 3D stack in ImageJ (File > Open).
Access Scaling Tool: Go to Image > Scale...
Configure Parameters:
X, Y, and Z Scales: Enter the desired Resampling Factor (e.g., 0.5 for 50% or 0.1 for 10%).
Interpolation: Select between None (Nearest Neighbor), Bilinear, or Bicubic.
Process: Ensure "Average when downsizing" is unchecked to strictly test the interpolation algorithms as described in the paper.
Save: Export the resulting stack as a .tiff for topological analysis (e.g., using BoneJ or Pore-Network Modeling).

# 4. How to Run the Test (Validation)
To replicate the accuracy tests shown in the manuscript (specifically for RF 0.5):
Baseline: Keep the original image at RF 1.0.
Execution: Run the scaling process three times on the original stack using RF 0.5, selecting a different interpolation method (Nearest Neighbor, Bilinear, and Bicubic) each time.
Comparison: * Measure the Mean Pore Diameter and Connected Porosity.
Compare the resampled results against the RF 1.0 baseline.
Threshold Check: Verify if the pore throats remain above the 3-voxel threshold. If a throat is reduced below 3 voxels, numerical occlusion (hydraulic collapse) is expected.
Example Output
When correctly executed, your ImageJ interface and resulting data should align with the sensitivity analysis illustrated below:
(Reference: Figure 7 from Silva et al., 2026, showing the transition from functional resolution to numerical occlusion as the Resampling Factor decreases.)

# 5. Contact
For questions regarding the methodology or data, please contact: Daiane Francisca do Nascimento Silva
Email: daiane.francisca@ufpe.br 
