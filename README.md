# SPCA-Net: Structural Prior-Guided Cross-Attention Network for OCT Fingerprint PAD

This repository is the official project page for the paper:

**Structural Prior-Guided Cross-Attention Network for OCT Fingerprint Presentation Attack Detection**  
Yi-Peng Liu, Jiajin Qi, Zhanqing Li, Jie Ji, Haohao Sun, Yilong Zhang, Haixia Wang, Jing Li

> **Status:** Under review / Major revision.  
> **Code Release:** We will release the full source code and pretrained models **upon acceptance/publication**.

---

## Abstract 
Fingerprint presentation attack detection (PAD) is critical for secure fingerprint recognition. OCT can capture subsurface 3D fingertip structures, offering stronger PAD cues. We propose a structural prior-guided cross-attention framework that leverages tissue-structure priors and jointly models segmentation-driven structural features and reconstruction-based distances. The method is trained without PA samples and generalizes well to diverse attack materials. A fused reconstruction-distance design further enlarges the separation between bona fide and PA samples for improved decision boundaries.

---

## Method
Our framework emphasizes subsurface tissue structural priors and integrates them into PAD representation learning:

- **Tissue-structure priors** from OCT B-scan segmentation
- **Cross-attention feature fusion** to enhance PAD-relevant structural information
- **Dual-distance spoof score** combining:
  - image reconstruction distance (**FDis**)
  - feature reconstruction distance (**RDis**)

---

## Dataset

Experiments are conducted on two OCT fingerprint PAD datasets: **ZJUT-EIFD** (in-house) and **U_OCFR** (public).

### ZJUT-EIFD (in-house)
Experiments are conducted on **ZJUT-EIFD** (OCT fingerprint dataset).

- OCT system: spectral-domain OCT, **central wavelength 1,310 nm**, bandwidth **85.6 nm**
- Each volume: **1,400 B-scans**; each B-scan: **500 × 1,800** pixels
- Bona fide: **60 participants**, total **2,039,800** fingerprint slices
- PA set: **525** PA sets fabricated from **21** distinct materials
- Due to incomplete early slices, only the **last 1,000 slices** per volume are used

**Segmentation subset**
- **1,050** manually annotated B-scans (glass / stratum corneum / viable epidermis)

> Note: Please refer to the paper for full dataset details and protocol.

---

### U_OCFR
The **U_OCFR** dataset was created by Zhang *et al.* and originates from their in-house OCT fingerprint database, comprising **2,449 OCT volumes**. The dataset provides OCT fingerprints in the form of volumetric data (instances/volumes): each instance typically consists of **400 B-scans** acquired along the fingertip in the horizontal (X–Y) direction, and each B-scan is a depth (X–Z) cross-section composed of multiple A-lines. Under the PAD protocol, the data are partitioned into a **reference set** and a **test set**, where the reference set is **not used for training**. The reference set contains **16 bona fide instances** from **eight fingers**, with each finger captured in **two acquisition sessions**; the test set includes **176 bona fide instances** from **137 subjects** and **121 PA instances**. The PA samples span **101 different materials** and include both **2D and 3D** presentation attacks, e.g., printing, pencil powder, crayon, and ink for 2D attacks, and transparent silica gel, gelatin, latex, and wood gum for 3D attacks.

**Cross-dataset evaluation (ZJUT → U_OCFR).**  
In our cross-dataset evaluation, we treat **U_OCFR** as an external target-domain test set to systematically assess the generalization capability of the proposed method under domain shift. Specifically, we keep the model architecture and parameters fixed and perform **no target-domain fine-tuning or adaptation**; instead, we directly deploy the model trained on our in-house dataset to **U_OCFR**. This setting enables us to evaluate **zero-shot generalization** under changes in acquisition conditions and shifts in the distribution of spoof types and materials.

**Reference**
- W. Zhang, H. Liu, F. Liu, and R. Ramachandra, “A Uniform Representation Learning Method for OCT-based Fingerprint Presentation Attack Detection and Reconstruction,” *Pattern Recognition*, vol. 149, Art. no. 109981, 2024.


---

## Metrics
We report standard PAD metrics, including:
- AUC / EER
- BPCER@APCER=10% (BPCER10), BPCER@APCER=20% (BPCER20)

---

## Code 
- The repository will be populated with:
  - training code
- **Release timeline:** upon acceptance/publication.

---

## Citation
If you find this work useful, please cite it:

```bibtex
@article{spcanet_oct_pad,
  title   = {Structural Prior-Guided Cross-Attention Network for OCT Fingerprint Presentation Attack Detection},
  author  = {Liu, Yi-Peng and Qi, Jiajin and Li, Zhanqing and Ji, Jie and Sun, Haohao and Zhang, Yilong and Wang, Haixia and Li, Jing},
  journal = {IEEE Transactions on Biometrics, Behavior, and Identity Science (TBIOM)},
  note    = {Under review},
  year    = {2025}
}
