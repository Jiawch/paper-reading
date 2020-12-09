# SPEECH

## TEXT TO SPEECH

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [s-Transformer: Segment-Transformer for Robust Neural Speech Synthesis](https://arxiv.org/abs/2011.08480) | 应该是 long-form | 
| 2.  | [TFGAN: Time and Frequency Domain Based Generative Adversarial Network for High-fidelity Speech Synthesis](https://arxiv.org/abs/2011.12206) | 这个很神奇，是哪个部件work呢，1) baseline 的setting is unfair, 2) for vibrations issue, use freq-D, 但除了mos微小的提升外，没有其他说明 vibrations 是freq-D解决的 |
| 3.  | [Parallel waveform synthesis based on generative adversarial networks with voicing-aware conditional discriminators](https://arxiv.org/abs/2010.14151) | cgan + lnner product, the input auxiliary features were up-sampled by nearest neighbor interpolation followed by 1-D convolutions so that the time resolution of the auxiliary features matched the sampling rate of the speech waveforms |
| 4.  | [END-TO-END ADVERSARIAL TEXT-TO-SPEECH](https://openreview.net/pdf?id=rsf1z-JSj87) | 1)DTW, 2)GAN-TTS, 3)projection embedding D,|
| 5.  | [High Fidelity Speech Synthesis with Adversarial Networks](https://arxiv.org/abs/1909.11646) | GAN-TTS |

## SINGVOIVE SYNTHESIS SYSTEM

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Learn2Sing: Target Speaker Singing Voice Synthesis by learning from a Singing Teacher](https://arxiv.org/abs/2011.08467) | tts -> svs，f0和duration建模, 用 GMM 对上述两者建模比 MSE 要好？就像 Wavenet 可以用 GMM 拟合 wave, domain-adaptation 对长音发挥作用 |
| 2.  | [Speech-to-Singing Conversion in an Encoder-Decoder Framework](https://arxiv.org/abs/2002.06595) | preserves some of its characteristics (e.g., speaker identity, linguistic content), while modifying certain others (melody, phoneme durations)，1）multispeaker用什么vocoder，Griffin-Lim 2）怎么 align speech and sing？直接通过变速拉伸，不管有没有align上， 3）Silent frame removal 模块 |
| 3.  | [Unsupervised Singing Voice Conversion](https://arxiv.org/abs/1904.06590) |  | 
| 4.  | [WGANSing: A Multi-Voice Singing Voice Synthesizer Based on the Wasserstein-GAN](https://arxiv.org/abs/1903.10729) | [code](https://github.com/pc2752/Multi_Voice_Sing_Speak_Sing), 看WGAN怎么实现的，1）输入和输出一样长，那一开始输入是怎么铺开到那么长的，用到 frame- wise phoneme annotations，和NPSS一样，原来WGANSING把duration，f0当成已知条件，先铺开 |
| 5.  | [A Combination of Model-based and Feature-based Strategy for Speech-to-Singing Alignment](https://www.isca-speech.org/archive/Interspeech_2019/pdfs/1942.pdf) | alignment approaches |
| 6.  | [A Dual Alignment Scheme for Improved Speech-to-Singing Voice Conversion](http://www.apsipa.org/proceedings/2017/CONTENTS/papers2017/15DecFriday/Poster%205/FA-P5.7.pdf) | alignment approache |
| 7.  | [A Universal Music Translation Network](https://arxiv.org/abs/1805.07848) | [code](https://github.com/facebookresearch/music-translation) the pitch of the input audio clip was changed locally |
| 8.  | [Speech-to-singing synthesis: Converting speaking voices to singing voices by controlling acoustic features unique to singing voices](https://staff.aist.go.jp/m.goto/PAPER/WASPAA2007saitou.pdf) | Model-based STS, non-nn model |
| 9.  | [Learning Singing From Speech](https://arxiv.org/pdf/1912.10128.pdf) | male，female 的转化，avg f0 |
| 10. | [I2R Speech2Singing Perfects Everyone’s Singing](https://www.isca-speech.org/archive/archive_papers/interspeech_2014/i14_2148.pdf) | Rhythm correction by DTW |

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


## TRANSFORM

| No. | Title | Thinking |
| --- | ---   | ---      |
| 1.  | [Multiple F0 Estimation in Vocal Ensembles using Convolutional Neural Networks](https://arxiv.org/abs/2009.04172) | F0建模，CQT变换 |


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
