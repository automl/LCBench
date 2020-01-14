# LCBench

A learning curve benchmark on openml data.

## Dataset overview

LCBench provides extensive training data for different architectures and hyperparameters evaluated on OpenML datasets. The current version provides 2000 configurations, each evaluated on 35 datasets over 50 epochs. Logs include for each epoch:

* Training, test and validation losses
* Training, test and validation accuracy
* Training, test and validation balanced accuracy
* Global gradient statistics (max, mean, median, norm, std, q10, q25, q75, q90)
* Layer-wise gradient statistics (max, mean, median, norm, std, q10, q25, q75, q90)
* Learning rate
* Runtime

And additionally:

* Configuration (architecture, hyperparameters)
* Number of model parameters
* Dataset statistics (number of classes, instances and features)

The data was created using [Auto-PyTorch](https://github.com/automl/Auto-PyTorch.git). All runs feature funnel-shaped MLP nets and use SGD with cosine annealing without restarts. Overall, 7 parameters were sampled at random (4 float, 3 integer). These are:

* Batch size: [16, 512], on log-scale
* Learning rate: [1e-4, 1e-1], on log-scale
* Momentum: [0.1, 0.99]
* Weight decay: [1e-5, 1e-1]
* Number of layers: [1, 5]
* Maximum number of units per layer: [64, 1024], on log-scale
* Dropout: [0.0, 1.0]


## Setup

Clone the git repository:

```sh
$ cd install/path
$ git clone ...
$ cd LCBench
```

Install requirements:

```sh
$ cat requirements.txt | xargs -n 1 -L 1 pip install
```

## Downloading the data


## Using the API

Loading the data:

```py
from LCBench import Benchmark

bench = Benchmark(data_dir="path/to/data.json")
```

Querying:

```py
bench.query(dataset_name="credit-g", tag="Train/loss", config_id=0)
```


## Examples

A jupyter notebook example is given in [API Example](add_link). For documentation you can also call help on the API methods or check the source.

## Tasks for the DL lecture 19/20
For the final project of the DL lecture, default tasks are defined in [notebooks](). Each notebook contains a short description of the task and a very basic example.
