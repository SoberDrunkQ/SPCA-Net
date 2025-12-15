# SPCA-Net: Structural Prior-Guided Cross-Attention Network for OCT Fingerprint PAD

This repository is the official project page for the paper:

**Structural Prior-Guided Cross-Attention Network for OCT Fingerprint Presentation Attack Detection**  
Yi-Peng Liu, Jiajin Qi, Zhanqing Li, Jie Ji, Haohao Sun, Yilong Zhang, Haixia Wang, Jing Li

> **Status:** Under review / Major revision.  
> **Code Release:** We will release the full source code **upon acceptance/publication**.

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

Experiments are conducted on two OCT fingerprint PAD datasets: **ZJUT-EIFD** (public) and **U_OCFR** (public).

### ZJUT-EIFD
Experiments are conducted on **ZJUT-EIFD** (OCT fingerprint dataset).

- OCT system: spectral-domain OCT, **central wavelength 1,310 nm**, bandwidth **85.6 nm**
- Each volume: **1,400 B-scans**; each B-scan: **500 × 1,800** pixels
- Bona fide: **60 participants**, total **2,039,800** fingerprint slices
- PA set: **525** PA sets fabricated from **21** distinct materials
- Due to incomplete early slices, only the **last 1,000 slices** per volume are used

**Segmentation subset**
- **1,050** manually annotated B-scans (glass / stratum corneum / viable epidermis)

> Note: Please refer to the paper for full dataset details and protocol.

**Reference**
- H. Sun, H. Wang, Y. Zhang, R. Liang, P. Chen, and J. Feng, “ZJUT-EIFD: A synchronously collected external and internal fingerprint database,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 46, no. 4, pp. 2267–2284, 2024.

### U_OCFR
We additionally evaluate on **U_OCFR** (external OCT fingerprint dataset) for cross-domain testing.

- **2,449** OCT volumes; each volume typically has **400 B-scans** (X–Y), each B-scan is an X–Z cross-section
- Split into **reference set** (not used for training) and **test set**
  - Reference: **16** bona fide (8 fingers × 2 sessions)
  - Test: **176** bona fide (137 subjects) + **121** PA
- PAIs cover **101** materials, including **2D/3D** attacks (e.g., printing/ink; silica gel/gelatin/latex)

> See the U_OCFR paper for full details and protocol.

**Reference**
- W. Zhang, H. Liu, F. Liu, and R. Ramachandra, “A Uniform Representation Learning Method for OCT-based Fingerprint Presentation Attack Detection and Reconstruction,” *Pattern Recognition*, vol. 149, Art. no. 109981, 2024.

### Cross-Domain Evaluation (ZJUT → U_OCFR)
In our cross-dataset evaluation, we treat **U_OCFR** as an external target-domain test set to systematically assess the generalization capability of the proposed method under domain shift. Specifically, we keep the model architecture and parameters fixed and perform **no target-domain fine-tuning or adaptation**; instead, we directly deploy the model trained on our in-house dataset to **U_OCFR**. This setting enables us to evaluate **zero-shot generalization** under changes in acquisition conditions and shifts in the distribution of spoof types and materials.

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
