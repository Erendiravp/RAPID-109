# RAPID-109
**RAt Pyramidal neuron Image Database (RAPID-109)** is a dataset of 109 low-resolution microscopy images of rat prefrontal cortex pyramidal neurons, acquired through experiments conducted at the Neuromodulation Laboratory, Institute of Physiology, BUAP. The dataset includes inverted-microscopy (40×) images and corresponding segmentation masks of live rat prefrontal pyramidal neurons. It contains JPG images, ground-truth PNG masks, and dilation-derived masks for training.

## Animals
Thirty-three 30-day-old male Wistar rats were sourced from the Claude Bernard Biotery at the Benemérita Universidad Autónoma de Puebla (BUAP, México). Animals had ad libitum access to food and water and were maintained under controlled environmental conditions (12:12 h light–dark cycle, constant temperature of 21 ◦C).

## File naming convention
Each image must match its mask by filename stem, e.g.:
- 'images_jpg/img_0001.jpg'
- 'masks_gt_png/img_0001.png'
- 'masks_dilated_r5_png/img_0001.png'

## Masks explained
### Ground-truth masks (GT)
'masks_gt_png/' contains **expert-annotated binary masks** used as ground truth for evaluation.

### Dilated masks (derived)
'masks_dilated_r5_png/' contains **derived masks** created by applying morphological dilation to the ground-truth masks using a **disk-shaped structuring element with radius r = 5 pixels**.
These masks are **NOT** ground truth; they were used as *training targets* in the dilation-enhanced setting, while **validation targets remained the original expert-annotated masks**.

## Reproducibility notes (as used in the manuscript)
- The segmentation workflow includes: image acquisition, expert mask annotation, optional mask dilation before training, model training (U-Net / Attention U-Net / Residual U-Net), and evaluation using DSC and qualitative inspection.
- In the experiments reported in the manuscript, the dataset was split 70/30 for train/validation and assessed with K-fold cross-validation (K=5).

## Citation
If you use this repository in your research, please cite the associated manuscript:

**Manuscript (under review):**  
[Author(s)], *Automatic classification of live pyramidal neurons in low-resolution inverted microscopy images using segmentation-derived representations*, manuscript under review, [Year].  
URL: [link to preprint or project page, if available]

**BibTeX**
```bibtex
@misc{vazquez2026manuscript,
  title        = {Automatic classification of live pyramidal neurons in low-resolution inverted microscopy images using segmentation-derived representations},
  author       = {Vazquez, Erendira and [Coauthor] and [Coauthor]},
  year         = {2026},
  note         = {Manuscript under review},
  howpublished = {\url{https://github.com/Erendiravp/[REPO_NAME]}},
}
