---
title: "Phrase-Based & Neural Unsupervised Machine Translation"
classes: wide
excerpt: "Work investigates how to learn to translate when having access to only monolingual corpora in each language."
tags: 
  - NMT
  - Unsupervised
  - Zero-Shot
  - Low-Resource
---

### Authors
Guillaume Lample, Myle Ott, Alexis Conneau, Ludovic Denoye, Marc’Aurelio Ranzato


## Overview
Data scarcity is among the main [challenges](https://arxiv.org/abs/1706.03872) for training a usable Neural Machine Translation(NMT) model. Despite the progress made for a high-resource language (such as; English-German) pair, most languages are characterized by the absence of parallel data to train an NMT system. As my first series of paper review and writing a post I will summarize the "Phrase-Based & Neural Unsupervised Machine Translation", to be presented at EMNLP18. Authors suggest two model variants; i) Phrase-based and ii) Neural. 


## Illustration
Both the Phrase-based and Neural rely on three core (#P1, #P2, and #P3) <b>principles</b>, consequently outperforming state-of-the-art approaches on unsupervised translation.     

![image-center](/assets/images/unsupervised-nmt-illustration.PNG){: .align-center}

  -- description source paper


## P1: Model Initialization
  - Aims to learn at least a word-by-word translation 
  - In the Neural case, i) jointly learn BPE model, ii) apply BPE, and iii) learning token embeedings to initialize the encoder-decoder lookup table, whereas for the Phrase-Based the initial phrase-tables are populated using a bilingual dictionary build from monolingual data (Conneau et al., 2018)
  - Note: if the languages are distant learning, learning bilingual dictioanry might be required in the Neural scenario. 
  
  - unlike the previous works that initialize   a prior that aims to train to models p<sub>s-t</sub> and p<sub>t-s</sbu> 

## P2: Language Modeling
 - Trains LM both for the source and target sides.
 - Used to apply substitution and word reordering, which is expected to improve the final translatoin task.
 - Denosing autoencoding strategy is used to train the LM's for the Neural, whereas KenLM is utilized to train an n-gram LM's for the Phrase-based approach.  

## P3: Iterative Back-Translation
  - Following [Sennrich et al., 2015](), the goal is to generate the source segments for the target monolingual data. 
  - The artificial source paired with the target creates a parallel data that will change the unsupervised task to a supervised one.
  - Thus, by repeating the inference stage with the latest model, the two models learns to generate a better source side artificial data. (See [here](https://arxiv.org/abs/1611.00179) for more on iterative-learning in a dual-task). 


## Algorithms
### Neural
  - 
<img src="/assets/images/algorithm_nmt.PNG" width="400">{: .align-center}


### Phrase-Based
  - 
<img src="/assets/images/algorithm_pbsmt.PNG" width="400">{: .align-center}

## Results
Experimental settings
  - Model: 

WMT14 En<>De
  - ...

WMT16 En<>Fr
  - ...
<img src="/assets/images/comparison_results.PNG" width="400">{: .align-center}


## More on Unsupervised MT
  - Please check out the following interesting works. 
  - Ravi and Knight (2011)
  - He et al., (2016)
  - Artetxe et al., (2018) 
  - Lample et al., (2018) 

## References

