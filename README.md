# Ovis-VL-Embedding
<div align="center">
  <img src=ovis_logo.png width="30%"/>
</div>
<br>

<p align="center">
  <a href="https://github.com/ATH-MaaS/Ovis-VL-Embedding"><img src="https://img.shields.io/badge/GitHub-Ovis--VL--Embedding-3157C8?logo=github" alt="github"></a>
  <a href="https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-9B"><img src="https://img.shields.io/badge/🤗_Model_Page-Ovis--VL--Embedding--9B-yellow" alt="model page 9B"></a>
  <a href="https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-2B"><img src="https://img.shields.io/badge/🤗_Model_Page-Ovis--VL--Embedding--2B-yellow" alt="model page 2B"></a>
  <a href="https://arxiv.org/pdf/2609.25165"><img src="https://img.shields.io/badge/📖_Technical_Report-arXiv-b31b1b.svg" alt="technical report"></a>
</p>

## Introduction

Ovis-VL-Embedding is a vision-language embedding model developed by the Alibaba ATH-MaaS team. It maps text, image, visual document, and video modalities into a unified representation space, enabling high-quality cross-modal retrieval and understanding.

**Ovis-VL-Embedding-9B** achieves leading performance on the [MMEB](https://huggingface.co/spaces/TIGER-Lab/MMEB) official leaderboard. It is a high-capacity vision-language embedding model for text, images, visual documents, video, and interleaved multimodal inputs, and is initialized from **Qwen3.5-9B**. It retains the native text and vision encoders together with the shared multimodal language backbone, removes the language-modeling head, and directly uses the final-layer hidden state at the last non-padding token as the retrieval embedding. No modality-specific projection head is added.

We also release **Ovis-VL-Embedding-2B**, a compact variant initialized from **Qwen3.5-2B**, which delivers strong text, image, document, and video retrieval under constrained serving budgets.

> Our technical report is now available on arXiv: [**arXiv:2609.25165**](https://arxiv.org/pdf/2609.25165). Model pages are also live on Hugging Face: [**ATH-MaaS/Ovis-VL-Embedding-9B**](https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-9B) and [**ATH-MaaS/Ovis-VL-Embedding-2B**](https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-2B). Model weights are not open-sourced yet and will be released in the near future. Stay tuned!

## Performance

### MMEB-v2

MMEB-v2 evaluates vision-language embeddings over **78 datasets** spanning image, video, and visual-document tasks.

| Group | Ovis-VL-Embedding-9B | Ovis-VL-Embedding-2B | Best compared baseline (9B) | Best compared baseline (2B) |
|:------|:--------------------:|:--------------------:|:---------------------------:|:---------------------------:|
| Image | **83.96** | 80.62 | 81.86 (+2.10) | 77.41 (+3.21) |
| Video | **72.90** | 67.12 | 75.95 (-3.05) | 68.84 (-1.72) |
| Visual document | **83.06** | 80.47 | 82.38 (+0.68) | 79.86 (+0.61) |
| **All 78 datasets** | **81.13** | **77.46** | 80.09 (**+1.04**) | 75.42 (**+2.04**) |

Ovis-VL-Embedding-9B achieves **81.13 overall**, outperforming the strongest compared baseline by **1.04 points**. Ovis-VL-Embedding-2B achieves **77.46 overall**, outperforming the strongest compared baseline in its scale group by **2.04 points**.

Both models rank first on all four image sub-tasks, video classification, video moment retrieval, the visual-document aggregate, and ViDoRe-V1. Scaling from 2B to 9B improves the overall score by **3.67 points**, with the largest gains on video question answering (+7.64), video moment retrieval (+7.23), and video retrieval (+5.74).

## Release
- [26/09/23] 🔥 Our [technical report](https://arxiv.org/pdf/2609.25165) is out, and the model pages of **Ovis-VL-Embedding-9B** and **Ovis-VL-Embedding-2B** are now live on Hugging Face. Model weights will be open-sourced soon.
- [26/09/09] 🔥 **Ovis-VL-Embedding-9B** released. Check out the [MMEB Leaderboard](https://huggingface.co/spaces/TIGER-Lab/MMEB) for results.
- [26/08/21] 🔥 **Ovis-VL-Embedding-v0.5** released and submitted to the [MMEB](https://huggingface.co/spaces/TIGER-Lab/MMEB) official leaderboard.
- [26/08/19] 🔥 Announcing Ovis-VL-Embedding, a vision-language embedding model for text, image, and video.

## Model

| Model | Parameters | Supported Modalities | Embedding Dim | Model Page | Tech Report |
|:------|:----------:|:--------------------:|:-------------:|:----------:|:-----------:|
| Ovis-VL-Embedding-9B | 9B | Text / Image / Visual Document / Video | 4096 | [🤗 HF](https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-9B) | [📖 arXiv](https://arxiv.org/pdf/2609.25165) |
| Ovis-VL-Embedding-2B | 2B | Text / Image / Visual Document / Video | 2048 | [🤗 HF](https://huggingface.co/ATH-MaaS/Ovis-VL-Embedding-2B)  | [📖 arXiv](https://arxiv.org/pdf/2609.25165) |

> **Note:** Ovis-VL-Embedding does not natively support audio input. Audio tracks within videos are not processed. For audio and general omni-modal retrieval, please use [**Ovis-Omni-Embedding-3B**](https://github.com/ATH-MaaS/Ovis-Omni-Embedding).

## Related Projects
- [**Ovis-Omni-Embedding**](https://github.com/ATH-MaaS/Ovis-Omni-Embedding): An omni-modal embedding model for text, image, visual document, video, and audio.

## Citation
If you find this work useful, please consider citing our technical report: [arXiv:2609.25165](https://arxiv.org/pdf/2609.25165).

## License
This project is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt) (SPDX-License-Identifier: Apache-2.0).

## Disclaimer
We used compliance-checking algorithms during the training process, to ensure the compliance of the trained model to the best of our ability. Due to the complexity of the data and the diversity of language model usage scenarios, we cannot guarantee that the model is completely free of copyright issues or improper content. If you believe anything infringes on your rights or generates improper content, please contact us, and we will promptly address the matter.
