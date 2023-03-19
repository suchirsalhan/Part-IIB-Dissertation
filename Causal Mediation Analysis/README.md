# Causal Analysis of Syntactic Agreement Mechanisms in Neural Language Models (Finlayson et al 2021)

This repository contains the data and code for replicating the results the total effect and attention head indirect effect experiments. This contains the relevant code from the open-source code-base developed by Finlyason et al (2021).  

Running this experiment is very computationally expensive, and can take hours on a GPU. The outputs also require gigabytes of space for the largest models. This is why I was unable to replicate the experiment and relied on the open-source results. 


Finlayson et al's code is based on the repository for [Vig et al. (2020)](https://github.com/sebastianGehrmann/CausalMediationAnalysis), but it differs primarily in that our code is written for subject-verb agreement evaluation sets, rather than gender bias datasets. Our code is written primarily for use with GPT-2, Transformer-XL, and XLNet, though as we use [huggingface transformers](https://github.com/huggingface/transformers/), this code should be extensible to other autoregressive language models as well.

## Requirements

`transformers==2.7`

## Data Templates
Templates are primarily based on [Lakretz et al. (2019)](https://github.com/FAIRNS/Number_and_syntax_units_in_LSTM_LMs).

| Structure | Template |
| --- | --- |
| Simple | The [noun] [verb] |
| 1 distractor | The [noun] [adv1] [verb] |
| 2 distractor | The [noun] [adv1] and [adv2] [verb] | 
| Across prepositional phrase | The [noun] [prep] the [prepnoun] [verb] |
| Across relative clause | The [noun] the [noun2] [verb2] [verb] | 
| Within relative clause | The [noun2] the [noun] [verb] |

Terminal values for [noun], [verb], etc., can be found in `vocab/wordlists`.

## Experiments

### Neuron interventions

To obtain neuron indirect effect and total effect numbers, run 
```
python neuron_experiment_multiple_templates_num_agreement.py \
<model> <device> <out_dir> <random_weights> <attractor> <seed> <examples>
```
from the root directory. We describe the arguments to this script here:

```
model: Which model to run experiments on
  distilgpt2 | gpt2 | gpt2-medium | gpt2-large | gpt2-xl 
| transfo-xl-wt103 | xlnet-base-cased

device: Device for pytorch
  cpu | cuda 

out_dir: Output directory for the results

random_weights: Whether to use a randomly initialized (untrained) model 
  random | not_random 

attractor: Which syntactic structure to use
  none | singular | plural | rc_singular | rc_plural | rc_singular_no_that
| rc_plural_no_that | within_rc_singular | within_rc_plural   
| within_rc_singular_no_that | within_rc_plural_no_that | distractor 
| distractor_1

seed: Integer random seed for reproducible results

examples: Integer number of examples to use from the template. 
  0 uses all examples. We use 300 in our paper.
```
Results are output to `results/<date>_neuron_intervention/<attractor>_<direct|indirect>_<model>.csv`
Once all outputs are obtained, running `python make_feathers.py <out_dir>/results` generates space-efficient `.feather` files from the `.csv` files. The `plots.ipynb` notebook assumes that results will be in this `.feather` format.

### Attention head interventions

To obtain attention head indirect effect results, run the `attention_intervention_structural.py` script. This script takes the same command-line arguments as the `neuron_experiment_multiple_templates_num_agreement.py` script.

Outputs are `.json` files in the `attention_results` directory.
