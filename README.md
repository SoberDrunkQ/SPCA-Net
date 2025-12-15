# SPCA-Net: Structural Prior-Guided Cross-Attention Network for OCT Fingerprint PAD

This repository is the official project page for the paper:

**Structural Prior-Guided Cross-Attention Network for OCT Fingerprint Presentation Attack Detection**  
Yi-Peng Liu, Jiajin Qi, Zhanqing Li, Jie Ji, Haohao Sun, Yilong Zhang, Haixia Wang, Jing Li

> **Status:** Under review / Major revision.  
> **Code Release:** We will release the full source code and pretrained models **upon acceptance/publication**.

---

## Abstract (paraphrased)
Fingerprint presentation attack detection (PAD) is critical for secure fingerprint recognition. OCT can capture subsurface 3D fingertip structures, offering stronger PAD cues. We propose a structural prior-guided cross-attention framework that leverages tissue-structure priors and jointly models segmentation-driven structural features and reconstruction-based distances. The method is trained without PA samples and generalizes well to diverse attack materials. A fused reconstruction-distance design further enlarges the separation between bona fide and PA samples for improved decision boundaries.

---

## Method Overview
Our framework emphasizes subsurface tissue structural priors and integrates them into PAD representation learning:

- **Tissue-structure priors** from OCT B-scan segmentation
- **Cross-attention feature fusion** to enhance PAD-relevant structural information
- **Dual-distance spoof score** combining:
  - image reconstruction distance (**FDis**)
  - feature reconstruction distance (**RDis**)

---

## Dataset
Experiments are conducted on **ZJUT-EIFD** (OCT fingerprint dataset).

- OCT system: spectral-domain OCT, **central wavelength 1,310 nm**, bandwidth 85.6 nm  
- Each volume: **1,400 B-scans**; each B-scan: **500 × 1,800** pixels  
- Bona fide: **60 participants**, total **2,039,800** fingerprint slices  
- PA set: **525** PA sets fabricated from **21** distinct materials  
- Due to incomplete early slices, only the **last 1,000 slices** per volume are used

**Segmentation subset**
- **1,050** manually annotated B-scans (glass / stratum corneum / viable epidermis)

> Note: Please refer to the paper for full dataset details and protocol.

---

## Metrics
We report standard PAD metrics, including:
- AUC / EER
- BPCER@APCER=10% (BPCER10), BPCER@APCER=20% (BPCER20)

---

## Code & Models
- The repository will be populated with:
  - training / evaluation code
  - pretrained checkpoints
  - scripts for reproducing tables and figures  
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
