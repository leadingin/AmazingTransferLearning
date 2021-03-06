This repository contains code for the paper [Learning by Association - A versatile semi-supervised training method for neural networks (CVPR 2017)](https://vision.in.tum.de/_media/spezial/bib/haeusser_cvpr_17.pdf) and the follow-up work [Associative Domain Adaptation (ICCV 2017)](https://vision.in.tum.de/_media/spezial/bib/haeusser_iccv_17.pdf)

The core functions are implemented in `semisup/backend.py`.
The files `train.py` and `eval.py` demonstrate how to use them. A quick example is contained in `mnist_train_eval.py`.

In order to reproduce the results from the paper, please use the architectures and pipelines from the `tools/{stl10,svhn,synth}.py`. They are loaded automatically by setting the flag `[target_]dataset` in `{train,eval}.py` accordingly.

Before you get started, please make sure to add the following to your `~/.bashrc`:
```
export PYTHONPATH=/path/to/learning_by_association:$PYTHONPATH
```

## Domain Adaptation Hyper parameters
### Synth. Signs -> GTSRB
```
"target_dataset": "gtsrb",
"walker_weight_envelope_delay": "0",
"max_checkpoints": 5,
"dataset": "synth_signs",
"visit_weight": "0.1",
"sup_per_batch": 24,
"walker_weight_envelope_steps": 1,
"eval_batch_size": 24,
"walker_weight_envelope": "linear",
"unsup_batch_size": 1032,
"visit_weight_envelope": "linear",
"decay_steps": 9000,
"sup_per_class": -1,
"max_steps": 12000,
"architecture": "svhn_model"
```

### MNIST -> MNIST-M
```
"target_dataset": "mnistm",
"walker_weight_envelope_delay": "500",
"max_checkpoints": 5,
"new_size": 32,
"dataset": "mnist3",
"visit_weight": "0.6",
"augmentation": true,
"walker_weight_envelope_steps": 1,
"walker_weight_envelope": "linear",
"unsup_batch_size": 1000,
"visit_weight_envelope": "linear",
"decay_steps": 9000,
"architecture": "svhn_model",
"sup_per_class": -1,
"sup_per_batch": 100,
"max_steps": "12000",
```

### SVHN -> MNIST
```
"target_dataset": "mnist3",
"walker_weight_envelope_delay": "500",
"max_checkpoints": 5,
"new_size": 32,
"dataset": "svhn",
"sup_per_batch": 100,
"decay_steps": 9000,
"unsup_batch_size": 1000,
"sup_per_class": -1,
"walker_weight_envelope_steps": 1,
"walker_weight_envelope": "linear",
"visit_weight_envelope": "linear",
"architecture": "svhn_model",
"visit_weight": 0.2,
"max_steps": "12000"
```

### Synth. Digits --> SVHN
```
"target_dataset": "svhn",
"walker_weight_envelope_delay": "2000",
"max_checkpoints": 5,
"dataset": "synth",
"sup_per_class": -1,
"sup_per_batch": 100,
"walker_weight_envelope_steps": 1,
"walker_weight_envelope": "linear",
"decay_steps": 9000,
"unsup_batch_size": 1000,
"visit_weight_envelope": "linear",
"architecture": "svhn_model",
"visit_weight": 0.2,
"max_steps": "20000",
```
