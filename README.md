<div align="center">

# Pig Brain MRI Atlas v2.0

**Averaged MRI brain templates, 26 labeled regions, and tissue probability maps for the 4-week-old and 12-week-old domestic pig (*Sus scrofa domestica*)**

[![Atlas version](https://img.shields.io/badge/atlas-v2.0-2a9d8f?style=for-the-badge)](https://pigmri.illinois.edu/neuroimaging-resources)
[![Released](https://img.shields.io/badge/released-2021--04--01-4361ee?style=for-the-badge)](https://pigmri.illinois.edu/neuroimaging-resources)
[![Ages](https://img.shields.io/badge/ages-4%20wk%20%7C%2012%20wk-e76f51?style=for-the-badge)](#at-a-glance)
[![Regions](https://img.shields.io/badge/regions-26-9b72cf?style=for-the-badge)](#labeled-regions)
[![License](https://img.shields.io/badge/license-CC%20BY--NC--ND%204.0-3fb950?style=for-the-badge)](LICENSE)

[![Paper](https://img.shields.io/badge/J%20Neurosci%20Methods-2021-ef8a62?style=flat-square)](https://doi.org/10.1016/j.jneumeth.2021.109107)
[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.jneumeth.2021.109107-blue?style=flat-square)](https://doi.org/10.1016/j.jneumeth.2021.109107)
[![PubMed](https://img.shields.io/badge/PubMed-33675840-326599?style=flat-square)](https://pubmed.ncbi.nlm.nih.gov/33675840/)
[![Format](https://img.shields.io/badge/format-NIfTI--1-555?style=flat-square)](https://nifti.nimh.nih.gov/nifti-1)
[![Website](https://img.shields.io/badge/website-pigmri.illinois.edu-13294B?style=flat-square)](https://pigmri.illinois.edu/)
[![Cite](https://img.shields.io/badge/cite-CITATION.cff-f2c14e?style=flat-square)](CITATION.cff)

</div>

> **A newer version is available.** [Version 2.1](https://github.com/Nutrition-Health-Neuroscience-DilgerLab/pig-brain-atlas-v2.1) (2023) adds three regions, corrects inconsistencies across the region thresholds, makes the not-brain map binary, and adds a 12-week FA template. Use v2.0 only to reproduce earlier work.

## Overview

This repository holds version 2.0 of the magnetic resonance imaging (MRI) brain atlases for the domestic pig at 4 and 12 weeks of age, as described in [Fil et al. (2021)](https://doi.org/10.1016/j.jneumeth.2021.109107). The atlases were built by the Piglet Nutrition & Cognition Laboratory (Department of Animal Sciences) together with the Biomedical Imaging Center at the Beckman Institute for Advanced Science and Technology, University of Illinois Urbana-Champaign, from scans of 20 artificially reared male pigs at 4 weeks of age and 13 sow-reared male pigs at 12 weeks of age.

Version 2.0 was posted on the [Pig Imaging Group website](https://pigmri.illinois.edu/neuroimaging-resources) on 1 April 2021. The files in `atlas/` are unpacked unchanged from the two official downloads, which are also attached to the [v2.0 release](https://github.com/Nutrition-Health-Neuroscience-DilgerLab/pig-brain-atlas-v2.0/releases/tag/v2.0) (about 17 MB together, versus 7.4 GB unpacked).

## At a glance

| | 4-week-old atlas | 12-week-old atlas |
|---|---|---|
| Matrix (voxels) | 160 × 200 × 160 | 256 × 256 × 256 |
| Voxel size | 0.5 mm isotropic | 1.0 mm isotropic |
| Labeled regions | 26 | 26 |
| ROI thresholds | 0, 25, 50% | 0, 25, 50% |
| Tissue classes | gray matter, white matter, CSF, not-brain | gray matter, white matter, CSF, not-brain |
| FA template | yes | no (added in v2.1) |
| Hemisphere masks | yes (left and right) | yes (left and right) |
| Uncompressed size | 1.5 GB | 5.8 GB |
| File format | NIfTI-1 (`.nii`) | NIfTI-1 (`.nii`) |

## Contents

```
.
├── atlas/
│   ├── 4wk/
│   │   ├── Pig_Brain_Atlas_4wk.nii                      averaged T1-weighted template
│   │   ├── Pig_FA_Standard_4wk.nii                      FA template for TBSS
│   │   ├── ROI Combined/
│   │   │   ├── Combined_4wk_thr{0,25,50}.nii            all regions in one label image
│   │   │   └── ROI_Labels.xlsx                          label number for each region
│   │   ├── Regions of Interest/
│   │   │   ├── ROI_thr{0,25,50}_4wk/<Region>_4wk_thr*.nii   one mask per region
│   │   │   └── {Left,Right}_Side_4wk.nii                hemisphere masks
│   │   └── Tissue Probability Maps/
│   │       └── {Gray_Matter,White_Matter,Cerebrospinal_fluid,NotBrain}_4wk.nii
│   └── 12wk/
│       ├── Pig_Brain_Atlas_12wk.nii
│       ├── ROI Combined/Combined_thr{0,25,50}_wk12.nii, ROI_Labels.xlsx
│       ├── Regions of Interest/ROI_thr{0,25,50}_wk12/<Region>_wk12_thr*.nii
│       ├── Regions of Interest/{Left,Right}_Side_12wk.nii     hemisphere masks
│       └── Tissue_Probability_Maps/{Gray_Matter,White_Matter,Cerebrospinal_Fluid,NotBrain}_12wk.nii
├── downloads/SHA256SUMS                                 checksums of the original archives
├── ATLAS_SHA256SUMS                                     checksum of every extracted file
├── CITATION.cff
├── LICENSE                                              CC BY-NC-ND 4.0
└── README.md
```

Folder and file names are kept exactly as they appear in the download, including the spaces in some folder names and the different age suffixes (`_4wk`, `_wk12`).

**Known issues fixed in v2.1.** In this version, the region masks hold values between 0 and 1 rather than strictly binary values, and values are not always consistent across the three thresholds. The not-brain maps hold values of 0 and −1. In the 12-week combined maps, the left and right superior colliculi (labels 14 and 25) have no voxels; use the separate masks for those regions. The two 4-week hemisphere masks have a slightly different voxel size in their headers (0.499 mm) from the rest of the 4-week files, and one voxel in the 12-week left hemisphere mask has the value 99 instead of 1. Version 2.1 does not include hemisphere masks.

## Labeled regions

The label numbers come from `ROI_Labels.xlsx`, which is the same for both ages.

| Label | Region | Label | Region |
|---:|---|---:|---|
| 1 | Cerebellum | 14 | Left superior colliculus |
| 2 | Cerebral aqueduct | 15 | Medulla |
| 3 | Corpus callosum | 16 | Midbrain |
| 4 | Fourth ventricle | 17 | Pons |
| 5 | Hypothalamus | 18 | Right caudate |
| 6 | Lateral ventricle | 19 | Right cortex |
| 7 | Left caudate | 20 | Right hippocampus |
| 8 | Left cortex | 21 | Right inferior colliculus |
| 9 | Left hippocampus | 22 | Right internal capsule |
| 10 | Left inferior colliculus | 23 | Right olfactory bulb |
| 11 | Left internal capsule | 24 | Right putamen and globus pallidus |
| 12 | Left olfactory bulb | 25 | Right superior colliculus |
| 13 | Left putamen and globus pallidus | 26 | Thalamus |

Version 2.1 renumbers the labels, so label numbers are not interchangeable between versions.

## Usage

**Integrity check.** To confirm that the atlas files are unchanged, run the following from the `atlas/` folder:

```bash
shasum -a 256 -c ../ATLAS_SHA256SUMS
```

## Version history

| Version | Released | Ages | Regions | Notes |
|---|---|---|---|---|
| [2.1](https://github.com/Nutrition-Health-Neuroscience-DilgerLab/pig-brain-atlas-v2.1) | 2023-07-21 | 4 wk, 12 wk | 29 | Current release. |
| **2.0** | 2021-04-01 | 4 wk, 12 wk | 26 | This repository. Updated 4-week atlas and the first 12-week atlas, described in Fil et al. (2021). |
| [1.2](https://github.com/Nutrition-Health-Neuroscience-DilgerLab/pig-brain-atlas-v1.2) | 2016-12-12 | 4 wk | 19 | Original 4-week atlas (Conrad et al., 2014). Released under CC0. |

## Citation

Please cite the article that describes the 4-week and 12-week atlases when using these files:

> Fil, J. E., Joung, S., Zimmerman, B. J., Sutton, B. P., & Dilger, R. N. (2021). High-resolution magnetic resonance imaging-based atlases for the young and adolescent domesticated pig (*Sus scrofa*). *Journal of Neuroscience Methods*, *354*, 109107. https://doi.org/10.1016/j.jneumeth.2021.109107

```bibtex
@article{fil2021pigatlas,
  title   = {High-resolution magnetic resonance imaging-based atlases for the young and adolescent domesticated pig (Sus scrofa)},
  author  = {Fil, Joanne E. and Joung, Sangyun and Zimmerman, Benjamin J. and Sutton, Bradley P. and Dilger, Ryan N.},
  journal = {Journal of Neuroscience Methods},
  volume  = {354},
  pages   = {109107},
  year    = {2021},
  doi     = {10.1016/j.jneumeth.2021.109107}
}
```

**Related resources.** [PigBET](https://github.com/Nutrition-Health-Neuroscience-DilgerLab/PigBET) is a deep learning tool for skull stripping and brain extraction in pig MRI, also distributed through the Pig Imaging Group website.

## Authors and contact

**Atlas authors (Fil et al., 2021):** Joanne E. Fil, Sangyun Joung, Benjamin J. Zimmerman, Bradley P. Sutton, and Ryan N. Dilger.

Questions about the atlases can be sent to Ryan N. Dilger, Department of Animal Sciences, University of Illinois Urbana-Champaign ([rdilger2@illinois.edu](mailto:rdilger2@illinois.edu)).

## License

The atlas files are licensed under the [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](https://creativecommons.org/licenses/by-nc-nd/4.0/) (CC BY-NC-ND 4.0); the full text is in [`LICENSE`](LICENSE). You may use and share them for noncommercial purposes, provided you cite Fil et al. (2021) and do not distribute modified versions of the atlas files.

Commercial use is not covered by this license. To discuss a commercial license, contact Ryan N. Dilger ([rdilger2@illinois.edu](mailto:rdilger2@illinois.edu)).
