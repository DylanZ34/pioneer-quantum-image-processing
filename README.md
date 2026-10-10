# Quantum image processing: FRQI and NEQR

Dylan Zhang — Pioneer Research Program, research with Professor Brenda Rubenstein (Brown University).

This project compares two quantum encodings of small astronomical images. The paper reports a trade-off between FRQI's 7 qubits and NEQR's 14 qubits for 8×8 grayscale images, using 20,000 simulator shots and comparing reconstructed images visually.

## Research question
How do FRQI and NEQR differ in qubit requirements and image retrieval for simplified astrophysical images?

## Structure
- `notebooks/quantum_image_processing.ipynb`: gallery-image experiment, copied from `Quantum_Image_Processing (3).ipynb`; selected because it contains both FRQI and NEQR with the locally available galaxy image.
- `notebooks/experiments/`: earlier morphology-data exploration from `uti8888.ipynb`; preserved as exploratory, not the paper's canonical run.
- `data/`: the small source galaxy JPG.
- `figures/`: plots extracted from retained notebook outputs.
- `docs/`: provenance and limitations.

## Setup and run
Notebook metadata records Python **3.11.9**. In a virtual environment:
```sh
python -m pip install -r requirements.txt
python -m jupyterlab notebooks/quantum_image_processing.ipynb
```
Use the notebook's directory as its working directory. Original installation cells are retained; after installing requirements, they need not be rerun. Image paths alone were adjusted in the working copy. All original scientific operations and existing outputs remain. Simulation and large circuit drawings may take time.

## Data and code sources
The paper's image source is [Astronomical Image and CSV Dataset](https://www.kaggle.com/datasets/mightyglow/astronomical-image-and-csv-dataset?resource=download). The local image is `spiral_galaxies_1.jpg`; obtain further paper images from that dataset. The paper credits adapted code from [Sharma-Siddhartha/FRQI-and-NEQR](https://github.com/Sharma-Siddhartha/FRQI-and-NEQR). Retain that attribution; no third-party license is inferred.

The exploratory notebook requires a 16.93 GB `5x64x64_training_with_morphology.hdf5`, excluded from git. Put it in `data/raw/` only after obtaining the exact dataset. [TODO: establish the source URL/version of this morphology file; it is not proven to be the same dataset as the paper's gallery images.] Older notebook versions, a byte-identical duplicate, the downloaded upstream ZIP/tutorial, full morphology CSVs, MNIST data, and private program reports/peer review are excluded.

## Paper and acknowledgments
[Paper](https://docs.google.com/document/d/1o3pIno_x4ieshtCcVsf8gb8NSjHjEKlNTEWFMuplVSU/edit)

Acknowledgments: Professor Brenda Rubenstein, Brown University, Pioneer Research Program, and the upstream code authors cited above. [TODO: describe Dylan's exact modifications and personal contribution.]

## Interpretation limits
This is a simulator study, not a measured quantum speedup or a hardware noise benchmark. The existing FRQI reconstruction rescales intensities by its maximum and a 1.15 brightness factor; the NEQR decode reverses coordinate bit strings and initializes unobserved pixels randomly. These choices warrant review before claiming exact fidelity. Packaging preserves them rather than silently changing the reported experiment. The paper contains images not all found in the selected notebook. Dependency imports and execution checks are documented in `docs/validation.md`.
