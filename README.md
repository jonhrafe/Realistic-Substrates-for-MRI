# Realistic Substrates for MRI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated library of **white matter microstructure substrates** for MRI simulation: physical phantoms, microscopy-based reconstructions, numerical substrate generators, the simulators that run on them, and the studies that used them.

Microstructural MRI is sensitive but not specific: a millimetre voxel averages axons, myelin, glia and vessels into a few signal curves, and every biophysical model splits those curves by assuming a tissue geometry. Substrates, tissue geometries whose ground truth is fully known, are how we test those assumptions. This list gathers the papers, tools and datasets behind them.

Companion material for the talk *"Realistic White Matter Microstructure Substrates"* (ISMRM White Matter Study Group, 2026).

**Contributions are welcome**: open an issue or a pull request (see [Contributing](#contributing)). Watch or star the repository to get updates.

## Contents

- [From our group](#from-our-group)
- [Reviews and foundations](#reviews-and-foundations)
- [Physical phantoms](#physical-phantoms)
- [Image-based substrates (microscopy reconstructions)](#image-based-substrates-microscopy-reconstructions)
- [Numerical substrate generators](#numerical-substrate-generators)
- [Simulators](#simulators)
- [Applications: what substrates taught us](#applications-what-substrates-taught-us)
- [Beyond diffusion and beyond axons](#beyond-diffusion-and-beyond-axons)
- [Datasets](#datasets)
- [History](#history)
- [Future directions](#future-directions)
- [Contributing](#contributing)

Tags used below: `generator` `simulator` `reconstruction` `phantom` `validation` `dataset` `review` `dMRI` `relaxation` `susceptibility` `MRS` `IVIM` `pathology`

---

## From our group

Signal Processing Laboratory (LTS5), EPFL, and collaborators.

| Work | Year | What it is | Links |
|---|---|---|---|
| **CACTUS**: Computational Axonal Configurations for Tailored and Ultradense Substrates. Villarreal-Haro, Gardier, Canales-Rodríguez, Fischi-Gomez, Girard, Thiran, Rafael-Patiño. *Front. Neuroinform.* | 2023 | `generator` White matter substrates by joint optimisation of capsule-chain fibres followed by fibre radial growth: up to 95% intra-axonal volume in (500 µm)³, crossings, dispersion, digital twins of EM samples. | [paper](https://doi.org/10.3389/fninf.2023.1208073) · [arXiv](https://arxiv.org/abs/2305.16109) · [code](https://github.com/Juanitovh/CACTUS) · [datasets](https://cactus.epfl.ch/) |
| **CACTUS 2.0**: towards a framework for generalised tissue modelling. Villarreal-Haro, Thiran, Rafael-Patiño | in prep. | `generator` `pathology` Biologically aware generator: compartments built in biological order with interactions (vessels, astrocytes, microglia, oligodendrocytes, neurons), literature-based tissue atlas, real-morphology import, progressive change (swelling, tumour growth). | coming soon |
| **MC/DC**: Robust Monte-Carlo simulations in diffusion-MRI: effect of the substrate complexity and parameter choice on the reproducibility of results. Rafael-Patiño, Romascano, Ramirez-Manzanares, Canales-Rodríguez, Girard, Thiran. *Front. Neuroinform.* | 2020 | `simulator` Open-source C++ Monte Carlo diffusion simulator for arbitrary meshes; convergence and reproducibility guidelines (walkers, step size, substrate size). | [paper](https://doi.org/10.3389/fninf.2020.00008) · [code](https://github.com/jonhrafe/MCDC_Simulator_public) · [docs](https://jonhrafe.github.io/MCDC_Simulator_public/) · [paper code](https://github.com/jonhrafe/Robust-Monte-Carlo-Simulations) |
| Axon morphology is modulated by the local environment and impacts the noninvasive investigation of its structure–function relationship. Andersson, Kjer, Rafael-Patiño, Pacureanu, Pakkenberg, Thiran, Ptito, Bech, Dahl, Dyrby. *PNAS* | 2020 | `reconstruction` `validation` X-ray nano-holotomography of monkey corpus callosum; segmented axons used as simulation substrates to show how morphology biases axon diameter estimates. | [paper](https://doi.org/10.1073/pnas.2012533117) · [dataset](https://www.drcmr.dk/axon-morphology-dataset) |
| The Art of Diffusion Simulations (ISMRM 2024 Diffusion Day). Rafael-Patiño | 2024 | `review` `simulator` Educational material on Monte Carlo diffusion simulations and substrates. | [material](https://github.com/jonhrafe/ISMRM2024_ArtSimulations) |
| Comparing STEAM and PGSE diffusion MRI signal of rat lymph nodes using in-silico simulations. Gardier, Villarreal-Haro, Canales-Rodríguez, Jelescu. *IEEE ISBI* | 2024 | `simulator` `dMRI` Substrates beyond white matter: lymph node simulations. | ISBI 2024 proceedings |

---

## Reviews and foundations

| Work | Year | Why read it |
|---|---|---|
| Fieremans & Lee. Physical and numerical phantoms for the validation of brain microstructural MRI: a cookbook. *NeuroImage* | 2018 | `review` `phantom` The reference review of both phantom families. [paper](https://doi.org/10.1016/j.neuroimage.2018.06.046) |
| Novikov, Fieremans, Jespersen, Kiselev. Quantifying brain microstructure with diffusion MRI: theory and parameter estimation. *NMR Biomed.* | 2019 | `review` `dMRI` "To model or to represent", the Standard Model of white matter. [paper](https://doi.org/10.1002/nbm.3998) |
| Alexander, Dyrby, Nilsson, Zhang. Imaging brain microstructure with diffusion MRI: practicality and applications. *NMR Biomed.* | 2019 | `review` `dMRI` Microstructure imaging in practice. [paper](https://doi.org/10.1002/nbm.3841) |
| Standard Model of diffusion in white matter: reproducibility | 2022 | `validation` [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC9248353/) |
| Mapping neurodegeneration with diffusion MRI: biomarkers | 2026 | `review` NODDI, CHARMED, SMT, WMTI, DBSI. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC13023135/) |
| Time-dependent diffusion MRI: a review | 2024 | `review` `dMRI` [paper](https://jzus.zju.edu.cn/article.php?doi=10.1631/jzus.A2400139) |

---

## Physical phantoms

| Work | Year | What it mimics | Links |
|---|---|---|---|
| Fieremans & Lee (review, Table 2) | 2018 | `phantom` Capillaries (intra-axonal), plain fibres (extra-axonal), hollow fibres (both). | [paper](https://doi.org/10.1016/j.neuroimage.2018.06.046) |
| Hubbard et al. Biomimetic phantom for the validation of diffusion magnetic resonance imaging (co-electrospun hollow fibres). *Magn. Reson. Med.* | 2014 | `phantom` Tunable fibre size distribution, both compartments. | [paper](https://doi.org/10.1002/mrm.25107) |
| Biomimetic white matter phantom (ISMRM abstract) | 2012 | `phantom` Early hollow-fibre phantom. | [abstract](https://cds.ismrm.org/protected/12MProceedings/PDFfiles/1939.pdf) |
| Physical hardware phantoms for diffusion MRI validation (ISMRM abstract) | 2016 | `phantom` Fibre and capillary phantoms. | [abstract](https://cds.ismrm.org/protected/16MProceedings/PDFfiles/7187.html) |

---

## Image-based substrates (microscopy reconstructions)

Image (X-ray, volume EM, light microscopy) → segment (increasingly with deep learning) → mesh → simulate inside real shapes.

| Work | Year | What it provides | Links |
|---|---|---|---|
| Kuan, Phelps et al. Dense neuronal reconstruction through X-ray holographic nano-tomography. *Nat. Neurosci.* | 2020 | `reconstruction` X-ray nano-holotomography pipeline. | [paper](https://doi.org/10.1038/s41593-020-0704-9) |
| Andersson et al. *PNAS* | 2020 | `reconstruction` Monkey corpus callosum, axons with their environment (vessels, cells, vacuoles). | [paper](https://doi.org/10.1073/pnas.2012533117) |
| Abdollahzadeh et al. Automated 3D axonal morphometry of white matter. *Sci. Rep.* | 2019 | `reconstruction` 3D EM morphometry of rat white matter. | [paper](https://doi.org/10.1038/s41598-019-42648-2) |
| Abdollahzadeh et al. DeepACSON: automated segmentation of white matter in 3D EM. *Commun. Biol.* | 2021 | `reconstruction` Deep-learning segmentation, ~20,000 myelinated axons per sample. | [paper](https://doi.org/10.1038/s42003-021-01699-w) |
| Lee et al. Along-axon diameter variation and axonal orientation dispersion revealed with 3D EM. *Brain Struct. Funct.* | 2019 | `reconstruction` `dMRI` | [paper](https://doi.org/10.1007/s00429-019-01844-6) |
| Lee et al. The impact of realistic axonal shape on axon diameter estimation using diffusion MRI. *NeuroImage* | 2020 | `validation` Calibre variation and undulation bias diameter estimates. | [paper](https://doi.org/10.1016/j.neuroimage.2020.117228) |
| Realistic Microstructure Simulator (RMS) | 2020 | `simulator` `reconstruction` Fast validation pipeline on EM-derived axons. | [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC8026575/) |
| Coronado-Leija et al. Volume electron microscopy in injured rat brain validates white matter microstructure metrics from diffusion MRI. *Imaging Neurosci.* | 2024 | `validation` `pathology` 3D EM against Standard Model estimates. | [paper](https://doi.org/10.1162/imag_a_00212) |
| Monte Carlo in realistic human intra-axonal space from EM (ISMRM #0845) | 2020 | `reconstruction` `simulator` | [abstract](https://cds.ismrm.org/protected/20MProceedings/PDFfiles/0845.html) |
| Extra-axonal time-dependent diffusion in injured rat white matter from 3D EM (ISMRM #0978) | 2022 | `reconstruction` `pathology` | [abstract](https://cds.ismrm.org/protected/22MProceedings/PDFfiles/0978.html) |
| Shapson-Coe et al. A petavoxel fragment of human cerebral cortex reconstructed at nanoscale resolution (H01). *Science* | 2024 | `reconstruction` `dataset` | [paper](https://doi.org/10.1126/science.adk4858) |
| Quantifying axonal features of human superficial white matter (128,285 axons) | 2025 | `reconstruction` | [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC12312701/) |

---

## Numerical substrate generators

| Generator | Year | Strategy | Highlights | Links |
|---|---|---|---|---|
| Hall & Alexander, Convergence and parameter choice for Monte-Carlo simulations of diffusion MRI. *IEEE TMI* | 2009 | packing | Gamma-distributed packed cylinders (Camino); the classic baseline. | [paper](https://doi.org/10.1109/TMI.2009.2015756) · [Camino](http://camino.cs.ucl.ac.uk/index.php?n=Tutorials.MCSimulator) |
| Close et al., A software tool to generate simulated white matter structures for the assessment of fibre-tracking algorithms (Numerical Fibre Generator). *NeuroImage* | 2009 | growth | Fibre-tracking phantoms. | [paper](https://doi.org/10.1016/j.neuroimage.2009.03.077) |
| Phantomas (Caruyer et al., ISMRM) | 2014 | analytic | Flexible software for diffusion MR phantoms. | [code](https://github.com/ecaruyer/phantomas) |
| AxonPacking (Mingasson et al.). *Front. Neuroinform.* | 2017 | packing | 2D packing with diameter distribution and g-ratio. | [paper](https://doi.org/10.3389/fninf.2017.00005) |
| Ginsburger et al., complex axonal geometry. *Front. Phys.* | 2018 | analytic | Undulation, beading, dispersion, nodes. | [paper](https://doi.org/10.3389/fphy.2018.00012) |
| MEDUSA (Ginsburger et al.). *NeuroImage* | 2019 | growth/packing | GPU, overlapping spheres; axons, astrocytes, oligodendrocytes. | [paper](https://doi.org/10.1016/j.neuroimage.2019.02.055) · [HPC campaigns](https://cds.ismrm.org/protected/22MProceedings/PDFfiles/2726.html) |
| ConFiG (Callaghan et al.). *NeuroImage* | 2020 | growth | Contextual fibre growth, one fibre at a time. | [paper](https://doi.org/10.1016/j.neuroimage.2020.117107) · [project](https://rcallagh.github.io/projects/config/) |
| **CACTUS** (Villarreal-Haro et al.). *Front. Neuroinform.* | 2023 | optimisation | Up to 95% ICVF at (500 µm)³; digital twins. | [paper](https://doi.org/10.3389/fninf.2023.1208073) · [code](https://github.com/Juanitovh/CACTUS) |
| White Matter Generator (Winther et al.). *Front. Neuroinform.* | 2024 | growth/dynamics | Interactive; glia reshape axons. | [paper](https://doi.org/10.3389/fninf.2024.1354708) |
| CATERPillar: a flexible framework for generating white matter numerical substrates with incorporated glial cells (Nguyen-Duc et al.). *bioRxiv* | 2025 | growth | Axons grown with branching glial cells. | [preprint](https://doi.org/10.1101/2025.06.20.660694) |
| **CACTUS 2.0** (Villarreal-Haro et al.) | in prep. | optimisation | Biologically aware, interacting compartments, progressive change. | coming soon |
| Palombo et al., generative model of realistic brain cells. *NeuroImage* | 2019 | growth | Neurons and glia morphologies for dMRI. | [paper](https://doi.org/10.1016/j.neuroimage.2018.12.025) |

---

## Simulators

| Simulator | Year | Notes | Links |
|---|---|---|---|
| **MC/DC** | 2020 | `simulator` C++, meshes and analytic shapes, convergence guidelines. | [paper](https://doi.org/10.3389/fninf.2020.00008) · [code](https://github.com/jonhrafe/MCDC_Simulator_public) |
| Camino | 2009 | `simulator` Classic Monte Carlo, cylinders and meshes. | [MC](http://camino.cs.ucl.ac.uk/index.php?n=Tutorials.MCSimulator) · [mesh](http://camino.cs.ucl.ac.uk/index.php?n=Tutorials.MCMeshSimulation) |
| Disimpy (Kerkelä et al.). *JOSS* | 2020 | `simulator` GPU Monte Carlo in Python. | [paper](https://doi.org/10.21105/joss.02527) · [code](https://github.com/kerkelae/disimpy) |
| GPU Monte Carlo in astrocytes from confocal microscopy (Nguyen et al.). *J. Magn. Reson.* | 2018 | `simulator` `reconstruction` Octree mesh acceleration. | [paper](https://cea.hal.science/cea-02155389/file/Nguyen_JMR_2018.pdf) |
| Microstructure Imaging Sequence Simulation Toolbox | — | `simulator` Numerical vs Monte Carlo approaches. | [paper](https://scispace.com/pdf/microstructure-imaging-sequence-simulation-toolbox-2atsehjfd3.pdf) |
| ISMRM MR-Hub catalogue | — | List of open MR simulation tools. | [site](https://ismrm.github.io/mrhub/) |

---

## Applications: what substrates taught us

| Finding | Year | Links |
|---|---|---|
| Mesoscopic structure of neuronal tracts from time-dependent diffusion: packing disorder sets the extra-axonal time dependence (Burcaw, Fieremans, Novikov). *NeuroImage* | 2015 | `dMRI` [paper](https://doi.org/10.1016/j.neuroimage.2015.03.061) |
| The importance of axonal undulation in diffusion MR measurements (Nilsson et al.). *NMR Biomed.* | 2012 | `dMRI` [paper](https://doi.org/10.1002/nbm.1795) |
| Realistic axonal shape (calibre variation, undulation) and diameter estimation (Lee et al.) | 2020 | `validation` [paper](https://doi.org/10.1016/j.neuroimage.2020.117228) |
| Local environment shapes axons and biases diameter estimates (Andersson et al.) | 2020 | `validation` [paper](https://doi.org/10.1073/pnas.2012533117) |
| Beading and undulation in axon diameter mapping | 2023 | `dMRI` [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC10153226/) · [follow-up](https://pubmed.ncbi.nlm.nih.gov/38168082/) |
| Sparse blind spherical deconvolution of diffusion weighted MRI (Fuchs et al.), evaluated on MC/DC-simulated signals. *Front. Neurosci.* | 2024 | `validation` [paper](https://doi.org/10.3389/fnins.2024.1385975) |
| Probing axonal swelling with time-dependent diffusion (Lee et al.) | 2019 | `pathology` [preprint](https://arxiv.org/pdf/1907.12685v1) |
| Simple estimate of axon size with diffusion MRI | 2020 | `dMRI` [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7949481/) |
| Digital twins of EM samples within ~2% of target volume fractions and g-ratio (CACTUS) | 2023 | `generator` `validation` [paper](https://doi.org/10.3389/fninf.2023.1208073) |
| Sensitivity and specificity of Standard Model estimates against volume EM (Coronado-Leija et al.) | 2024 | `validation` [paper](https://doi.org/10.1162/imag_a_00212) |

---

## Beyond diffusion and beyond axons

| Work | Year | Contrast / structure | Links |
|---|---|---|---|
| Palombo et al., new paradigm to assess brain cell morphology by diffusion-weighted MRS. *PNAS* | 2016 | `MRS` Realistic cell morphologies. | [paper](https://doi.org/10.1073/pnas.1504327113) |
| Wharton & Bowtell, Fiber orientation-dependent white matter contrast in gradient echo MRI. *PNAS* | 2012 | `susceptibility` Hollow-cylinder myelin model. | [paper](https://doi.org/10.1073/pnas.1211075109) |
| Soma size and SANDI simulations (Palombo et al.) | 2021 | `dMRI` Soma and neurites. | [paper](https://discovery.ucl.ac.uk/id/eprint/10132211/1/Palombo_1-s2.0-S1053811921006996-main.pdf) |
| Schiavi et al., Mapping tissue microstructure across the human brain on a clinical scanner with soma and neurite density image metrics (SANDI). *Hum. Brain Mapp.* | 2023 | `dMRI` | [paper](https://doi.org/10.1002/hbm.26416) |
| Spherical permeable cell substrates | 2022 | `dMRI` exchange | [preprint](http://arxiv.org/pdf/2209.02293) |
| Dendritic spines vs exchange in time dependence | 2025 | `dMRI` | [preprint](https://arxiv.org/pdf/2504.21537) |
| Towards a Standard Model with phase and relaxation: a Monte Carlo study (ISMRM #0589) | 2024 | `relaxation` `susceptibility` | [abstract](https://archive.ismrm.org/2024/0589.html) |

---

## Datasets

| Dataset | Links |
|---|---|
| CACTUS substrates (meshes, multiple sizes and densities) | [cactus.epfl.ch](https://cactus.epfl.ch/) |
| Axon Morphology Dataset (vervet monkey, X-ray nano-holotomography) | [DRCMR](https://www.drcmr.dk/axon-morphology-dataset) |
| H01 human cortex EM | [paper](https://doi.org/10.1126/science.adk4858) |
| XPRESS challenge (X-ray holographic nano-tomography) | [paper](https://ar5iv.labs.arxiv.org/html/2302.03819) |

---

## History

| Work | Year | Why it matters |
|---|---|---|
| Lipinski H-G. Monte Carlo simulation of extracellular diffusion in brain tissues. *Phys. Med. Biol.* 35:441–447 | 1990 | First "segment, then simulate": 2D histology thresholded into cells and extracellular space, random walks to estimate tortuosity, run on a DEC LSI-11/73. [paper](https://doi.org/10.1088/0031-9155/35/3/012) |
| Stikov et al. In vivo histology of the myelin g-ratio with MRI. *NeuroImage* | 2015 | EM targets later reproduced by digital twins. [paper](https://doi.org/10.1016/j.neuroimage.2015.05.023) |

---

## Future directions

| Work | Year | Links |
|---|---|---|
| Reconstructing the human brain's wiring diagram from axons up | 2025 | [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC12695016/) |
| Deep learning multi-fibre estimation and uncertainty. *Med. Image Anal.* | 2025 | [paper](https://pubmed.ncbi.nlm.nih.gov/40112509/) |
| Implicit neural representations for Standard Model estimation | 2025 | [preprint](https://arxiv.org/html/2506.15762v1) |
| New imaging technologies for multiscale connectomics (MPI) | 2025 | [event](https://www.bi.mpg.de/events/42317/2867) |

---

## Contributing

Suggestions are very welcome. Please open an issue, or a pull request adding one row to the right table with: authors (short), title, venue, year, tags, and a DOI or stable link (code and data links if available). See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related rights to this list.
