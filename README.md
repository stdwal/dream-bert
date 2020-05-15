A BERT-Based Machine Reading Comprehension Baseline
------------------------------------------------------

This repository maintains a machine reading comprehension baseline based on [BERT](https://arxiv.org/abs/1810.04805). The implementations follow the baseline system descriptions in the following two papers. 

* [Improving Question Answering with External Knowledge](https://arxiv.org/abs/1902.00993)
* [Probing Prior Knowledge Needed in Challenging Chinese Machine Reading Comprehension](https://arxiv.org/abs/1904.09679)

If you find this code useful, please consider citing the following papers.

```
@article{sun2019probing,
  title={Probing Prior Knowledge Needed in Challenging Chinese Machine Reading Comprehension},
  author={Sun, Kai and Yu, Dian and Yu, Dong and Cardie, Claire},
  journal={CoRR},
  volume={cs.CL/1904.09679v2},
  url={https://arxiv.org/abs/1904.09679v2}
  year={2019}
}

@article{pan2019improving,
  title={Improving Question Answering with External Knowledge},
  author={Pan, Xiaoman and Sun, Kai and Yu, Dian and Ji, Heng and Yu, Dong},
  journal={CoRR},
  volume={cs.CL/1902.00993v1}
  url={https://arxiv.org/abs/1902.00993v1},
  year={2019}
}

```

Here, we show the usage of this baseline using a demo designed for [DREAM](https://dataset.org/dream/), a dialogue-based three-choice machine reading comprehension task.

  1. Download and unzip the pre-trained language model from https://github.com/google-research/bert. and set up the environment variable for BERT in ```run.sh``` by ```export BERT_BASE_DIR=/PATH/TO/BERT/DIR```.
  2. Copy the data folder ```data``` from the [DREAM repo](https://github.com/nlpdata/dream) to ```data/dream```.
  3. run ```bash run.sh```
  4. The resulting fine-tuned model, predictions, and evaluation results are stored in ```dream_finetuned```.

**Results on DREAM**:

We run the experiments five times with different random seeds and report the best development set performance and the corresponding test set performance. 

| Method/Language Model | Batch Size | Learning Rate | Epochs | Dev  | Test |
| --------------------  | ---------- | ------------- | ------ | ---  | ---- |
| BERT-Base, Uncased    | 24         | 2e-5          | 8      | 63.4 | 63.2 |
| BERT-Large, Uncased   | 24         | 2e-5          | 16     | 66.0 | 66.8 |
| [Human Performance](https://arxiv.org/abs/1902.00164v1)     |            |               |        | 93.9 | 95.5 |
| [Ceiling Performance](https://arxiv.org/abs/1902.00164v1)   |            |               |        | 98.7 | 98.6 |


**Environment**: The code has been tested with Python 3.6 and PyTorch 1.0
