# Part-IIB-Dissertation-Code
This is the code associated with a dissertation submitted for Part IIB of the Linguistics Tripos in March 2023, which will appear in Volume 15 of the "Cambridge Occasional Papers in Linguistics". 

# Grammatical Error Detection Probe
## Content of Main Folder: Probing Results
This contains a sample of the **Grammatical Error Detection** probing results for *Layer 12 of BERT* (Devlin et al 2019). All probing experiments cited were run in the Computer Lab in research supported by Cambridge University Press & Assessment.  The per-layer probing results were personally shared by Chris Davis and Andrew Caines for further analysis in this dissertation. 

The F1-macro scores were reported in the dissertation text. 

## Marvin & Linzen Stimuli
The targeted syntactic evaluation dataset developed by **Marvin & Linzen (2018)** is included in the folder. 


## Training Data
The W&I-FCE corpus used to train the GED probe is available here: https://www.cl.cam.ac.uk/research/nl/bea2019st/ 

### Cambridge English Write & Improve
Write & Improve (Yannakoudakis et al., 2018) is an online web platform that assists non-native English students with their writing. Learners submit letters, stories, articles and essays in response to various prompts, and the W&I system provides instant feedback. The corpus comprises of annoated W&I  submissions, each assigned a CEFR level.

### LOCNESS

The LOCNESS corpus (Granger, 1998) consists of essays written by native English students. It was originally compiled by researchers at the Centre for English Corpus Linguistics at the University of Louvain. The W&I annotators to anontated a subsection of LOCNESS so researchers can test the effectiveness of their systems on the full range of English levels and abilities.

### ERRANT Annotation Tool
This repository contains the grammatical ERRor ANnotation Toolkit (ERRANT) can be found here: 
https://github.com/chrisjbryant/errant

### Additional GED Dataset
This folder contains examples of the GED Predictions when evaluated sentences in Marvin & Linzen dataset according to different agreement attraction stimuli. 

# Causal Mediation Analysis
The code for **causal mediation analysis** experiment developed by Finlayson et al (2021) is included. It was not replicated as this causal mediation analysis is very computationally expensive– the authors note that it “can  take hours on a GPU. The outputs also require gigabytes of space for the largest models.”

# Multimodal CLIP Experiments Code
A selection of the code from Salhan, Liu & Collier (2022/forthcoming) for intrinsic semantic evaluation of multimodal CLIP is also included along with a pre-print. 
