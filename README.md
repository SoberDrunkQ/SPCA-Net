# SPCA-Net: Structural Prior-Guided Cross-Attention Network for OCT Fingerprint PAD

This repository is the official project page for the paper:

**Structural Prior-Guided Cross-Attention Network for OCT Fingerprint Presentation Attack Detection**  
Yi-Peng Liu, Jiajin Qi, Zhanqing Li, Jie Ji, Haohao Sun, Yilong Zhang, Haixia Wang, Jing Li

> **Status:** Under review / Major revision.  
> **Code Release:** We will release the full source code and pretrained models **upon acceptance/publication**.

---

## Abstract 
Fingerprint presentation attack detection (PAD) is crucial in automatic fingerprint recognition systems. Optical coherence tomography (OCT) can capture the 3D complex structure of a fingertip because of its high resolution and skin penetrability, thus providing more reliable PAD performance for fingerprint recognition technology. Unsupervised OCT fingerprint PAD remains an unresolved issue. Existing methods rely primarily on whole slices of OCT volume and often overlook the importance of continuity and correlation among multiple features beneath the skin. In this study, we explore the reconstruction and segmentation tasks for OCT B-scan slices to discover the potential relationships between the multilayer tissue structure and overall features, and their implications for PAD tasks. We propose a novel cross-attention network that leverages prior knowledge of fingertip tissue structure. This network enhances the PAD performance by incorporating a cross-attention segmentation task interaction module to capture more structural information. Notably, our method does not require presentation attack (PA) samples during training and exhibits good generalizability for PA samples made from various materials during testing. Moreover, we introduce a reconstruction loss, which is used to further widen the reconstruction distance between the bona fide and PA samples to obtain a more accurate decision boundary for the PAD task.

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
