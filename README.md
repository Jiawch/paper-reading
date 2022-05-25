# SPEECH

## TEXT TO SPEECH

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [s-Transformer: Segment-Transformer for Robust Neural Speech Synthesis](https://arxiv.org/abs/2011.08480) | long-form 相关 | 
| 2.  | [TFGAN: Time and Frequency Domain Based Generative Adversarial Network for High-fidelity Speech Synthesis](https://arxiv.org/abs/2011.12206) | 这个不大认同，不知是哪个部件 work，1) baseline 的setting is unfair, 2) for vibrations issue, 作者使用了 freq-D, 但除了mos微小的提升外，没有其他说明 vibrations 是 freq-D 解决的 3) 根据以前的经验，直接在 vocoder 的 频谱做判别，并不会带来惊艳的效果，不直接 |
| 3.  | [Parallel waveform synthesis based on generative adversarial networks with voicing-aware conditional discriminators](https://arxiv.org/abs/2010.14151) | 对 pwg D 的改进，1) 大感受野，covers long-term variations of the harmonic component & penalizes any unwanted aperiodic noise components, 2) 小卷积核，focus on the detailed high-frequency, because the charac- teristics of the noise component vary rapidly. 3) 在我看来真正 work 的是 condition 和 大的卷积核 |
| 4.  | [END-TO-END ADVERSARIAL TEXT-TO-SPEECH](https://openreview.net/pdf?id=rsf1z-JSj87) | 1)DTW, 2)GAN-TTS, 3)projection embedding D,|
| 5.  | [High Fidelity Speech Synthesis with Adversarial Networks](https://arxiv.org/abs/1909.11646) | GAN-TTS |
| 6.  | [A Spectral Energy Distance for Parallel Speech Synthesis](https://arxiv.org/pdf/2008.01160.pdf) | 他加不同noise，我们可不可以加不同phase |
| 7.  | [A Spectral Energy Distance for Parallel Speech Synthesis](https://arxiv.org/pdf/2008.01160.pdf) | STFT loss额外加了一个 repulsive term 解决电音 |
| 8.  | [DiffWave: A Versatile Diffusion Model for Audio Synthesis](https://openreview.net/forum?id=a-xFK8Ymz5J) | 新的生成模型 |
| 9.  | [EfficientTTS: An Efficient and High-Quality Text-to-Speech Architecture](https://arxiv.org/pdf/2012.03500.pdf) | 这个paper 也挺有意思   做alignment的, 可能可以丰富EATS上次那个DTW的做法   |

## SINGVOIVE SYNTHESIS SYSTEM

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Learn2Sing: Target Speaker Singing Voice Synthesis by learning from a Singing Teacher](https://arxiv.org/abs/2011.08467) | tts -> svs，1）f0 和 duration 建模, 2）用 GMM 对上述两者建模比 MSE 要好？就像 Wavenet 可以用 GMM 拟合 wave, 3）domain-adaptation 对长音发挥作用 |
| 2.  | [Speech-to-Singing Conversion in an Encoder-Decoder Framework](https://arxiv.org/abs/2002.06595) | [code](https://github.com/jayneelparekh/sp2si-code)preserves some of its characteristics (e.g., speaker identity, linguistic content), while modifying certain others (melody, phoneme durations)，1）multispeaker用什么vocoder，Griffin-Lim 2）怎么 align speech and sing？直接通过变速拉伸，不管有没有align上， 3）Silent frame removal 模块 |
| 3.  | [Unsupervised Singing Voice Conversion](https://arxiv.org/abs/1904.06590) |  | 
| 4.  | [WGANSing: A Multi-Voice Singing Voice Synthesizer Based on the Wasserstein-GAN](https://arxiv.org/abs/1903.10729) | [code](https://github.com/pc2752/Multi_Voice_Sing_Speak_Sing), 1）输入和输出一样长，那一开始输入是怎么铺开到那么长的，用到 frame- wise phoneme annotations，和NPSS一样，原来WGANSING把duration，f0当成已知条件，先铺开 |
| 5.  | [A Combination of Model-based and Feature-based Strategy for Speech-to-Singing Alignment](https://www.isca-speech.org/archive/Interspeech_2019/pdfs/1942.pdf) | alignment approaches |
| 6.  | [A Dual Alignment Scheme for Improved Speech-to-Singing Voice Conversion](http://www.apsipa.org/proceedings/2017/CONTENTS/papers2017/15DecFriday/Poster%205/FA-P5.7.pdf) | alignment approache |
| 7.  | [A Universal Music Translation Network](https://arxiv.org/abs/1805.07848) | [code](https://github.com/facebookresearch/music-translation) 1）the pitch of the input audio clip was changed locally |
| 8.  | [Speech-to-singing synthesis: Converting speaking voices to singing voices by controlling acoustic features unique to singing voices](https://staff.aist.go.jp/m.goto/PAPER/WASPAA2007saitou.pdf) | Model-based STS, non-nn model |
| 9.  | [Learning Singing From Speech](https://arxiv.org/pdf/1912.10128.pdf) | male，female 的转化，avg f0 |
| 10. | [I2R Speech2Singing Perfects Everyone’s Singing](https://www.isca-speech.org/archive/archive_papers/interspeech_2014/i14_2148.pdf) | Rhythm correction by DTW |
| 11. | [DATA EFFICIENT VOICE CLONING FOR NEURAL SINGING SYNTHESIS](https://arxiv.org/pdf/1902.07292.pdf) | learned speaker embedding，对 new speakers 策略；finetune 策略 |
| 12. | [HMM-based singing voice synthesis system using pitch-shifted pseudo training data](https://www.isca-speech.org/archive/archive_papers/interspeech_2010/i10_0845.pdf) | singing alignment, Pitch-shifted Pseudo Training |
| 13. | [A Strategy for Improved Phone-Level Lyrics-to-Audio Alignment for Speech-to-Singing Synthesis](https://pdfs.semanticscholar.org/bdbd/c1dec8478ebab35c80fd7cf73f9765519a3d.pdf)，[Applying Spectral Normalisation and Efficient Envelope Estimation and Statistical Transformation for the Voice Conversion Challenge 2016](http://www.cstr.ed.ac.uk/downloads/publications/2016/0305.PDF) | Post-processing 把 pitch scale 从 singing 变到 speech 上来，那我们可不可以反变换, phase correction model，可以帮助vocoder？ |

## SEPARATION

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Probabilistic Permutation Invariant Training for Speech Separation](https://arxiv.org/pdf/1908.01768.pdf) | PIT 的改进, 可以去看下 PIT 的代码 |
| 2.  | [Permutation Invariant Training of Deep Models for Speaker-Independent Multi-talker Speech Separation](https://arxiv.org/abs/1607.00325), [Multi-talker Speech Separation with Utterance-level Permutation Invariant Training of Deep Recurrent Neural Networks](https://arxiv.org/abs/1703.06284) | PIT, utterance-level PIT |
| 3.  | [IMPLICIT FILTER-AND-SUM NETWORK FOR MULTI-CHANNEL SPEECH SEPARATION](https://arxiv.org/abs/2011.08401) | multi-channel |
| 4.  | [RETHINKING THE SEPARATION LAYERS IN SPEECH SEPARATION NETWORKS](https://arxiv.org/abs/2011.08400) | cascade, 无 teacher force，提到但未实验 speaker number 可以是  |
| 5.  | [Listening and Grouping: An Online Autoregressive Approach for Monaural Speech Separation](https://kar.kent.ac.uk/71467/1/version10_lzx_ivm.pdf) | 可能与cascade 相关 |
| 6.  | [Divide and Conquer: A Deep CASA Approach to Talker-independent Monaural Speaker Separation](https://arxiv.org/abs/1904.11148) | 可能与cascade 相关 |
| 7.  | [A comprehensive study of speech separation: spectrogram vs waveform separation](https://arxiv.org/pdf/1905.07497.pdf) | BSS 综述 |
| 8.  | [Research Advances and Perspectives on the Cocktail Party Problem and Related Auditory Models](http://html.rhhz.net/ZDHXBZWB/html/2019-2-234.htm) | 鸡尾酒会综述 | 
| 9.  | [Recursive speech separation for unknown number of speakers](https://arxiv.org/pdf/1904.03065.pdf) | unknown speaker number |
| 10. | [ONE SHOT LEARNING FOR SPEECH SEPARATION](https://arxiv.org/pdf/2011.10233.pdf) | 这个是不是说明 meta-learning 放在source domain和taget domain相差不大的时候，比style transform好 |
| 11. | [Serialized Output Training for End-to-End Overlapped Speech Recognition](https://arxiv.org/pdf/2003.12687.pdf)、[STREAMING MULTI-SPEAKER ASR WITH RNN-T](https://arxiv.org/pdf/2011.11671.pdf) | 有意思，ASR 里 SOT(first-in, first-out) 比 PIT 好，2020的方法，还没有人做 |
| 12. | [Applying Spectral Normalisation and Efficient Envelope Estimation and Statistical Transformation for the Voice Conversion Challenge 2016](http://www.cstr.ed.ac.uk/downloads/publications/2016/0305.PDF) | 一个比线性回归更好的 envelope 模型？ |
| 13. | [Mixup-breakdown: a consistency training method for improving generalization of speech separation models](https://arxiv.org/pdf/1910.13253.pdf) | mixup 用在separation 会怎么样 |


## leverages additional speaker information to help spearation

- information from target speaker 

wavesplit: not solely optimized for identification but also for the reconstruction of separated speech
wavesplit: loss 关联到 replusive loss, 简化kmeans，使其可也end2end也很妙；和vq-vae很像，有什么关联
LPC（线性预测编码）: 与文本有关

| No. | Title | Thinking |
| --- | ---   | ---      |


## TRANSFORM

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Multiple F0 Estimation in Vocal Ensembles using Convolutional Neural Networks](https://arxiv.org/abs/2009.04172) | F0建模，CQT变换 |
| 2.  | [UPSAMPLING ARTIFACTS IN NEURAL AUDIO SYNTHESIS](https://arxiv.org/pdf/2010.14356.pdf) |  这篇专门分析上采样的问题 | 


## LONG-FORM

| No. | Title | Thinking |
| --- | ---   | ---      |


## Others are relate to speech

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [VOCAL MELODY EXTRACTION USING PATCH-BASED CNN](https://arxiv.org/pdf/1804.09202.pdf) | melody/F0 extractor |
| 2.  | [FastPitch: Parallel Text-to-speech with Pitch Prediction](https://arxiv.org/abs/2006.06873) | Pitch modeling, 与fs2不同，它是在铺开前预测 average pitch of every character，我好奇这个 avg pitch 的 target 是怎么得来的 |


# Computer Vision

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Wavelet Integrated CNNs for Noise-Robust Image Classification](https://arxiv.org/pdf/2005.03337.pdf) |  |


# Flow
| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | | |


# Phase
| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [GANSYNTH: ADVERSARIAL NEURAL AUDIO SYNTHESIS](https://arxiv.org/pdf/1902.08710.pdf), [LEARNING AUDIO REPRESENTATIONS VIA PHASE PREDICTION ](https://arxiv.org/pdf/1910.11910.pdf) | [Demo](https://google.github.io/phase-prediction/)这两paper直接预测了相位 |
| 2.  | [Phase reconstruction based on recurrent phase unwrapping with deep neural networks](https://arxiv.org/pdf/2002.05832.pdf) | instantaneous frequency（IF） 和 group delay（GD）估计phase |

# Transducer
| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Sequence Transduction with Recurrent Neural Networks](https://arxiv.org/pdf/1211.3711.pdf), [FastEmit: Low-latency Streaming ASR with Sequence-level Emission Regularization](https://arxiv.org/pdf/2010.11148.pdf) | rnnt |
| 2.  | [Initial investigation of an encoder-decoder end-to-end TTS framework using marginalization of monotonic hard latent alignments](http://128.84.4.27/pdf/1908.11535) | transducer tts |


# Speech Feature
| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Comparison of Time-Frequency Representations for Environmental Sound Classification using Convolutional Neural Networks](https://arxiv.org/pdf/1706.07156.pdf) | |

# peking opera
| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Synthesising Expressiveness in Peking Opera via Duration Informed Attention Network](https://arxiv.org/pdf/1912.12010.pdf) |  |

# Code
[HiFiSinger](https://github.com/CODEJIN?tab=overview&from=2020-11-01&to=2020-11-30)

