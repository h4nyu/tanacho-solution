# tanacho-solution

## requirements

* docker
* docker-compose
* nvidia-docker 


## setup

1. Setup `.env` file
```
TENSORBOARD_PORT=6006
```

1. Build environment image

```sh
docker-compose build app
```

1. Setup dataset
```
datasets/
├── evaluation
├── readme
├── sample_submit
├── train
└── train_meta.json
```

1. Enter the app container

```sh
docker-compose rm -rm app bash
```

1. Create extra samples

```sh
python cli.py extend
```

1. Train model

```sh
python cli.py train -c configs/v2-1.yaml
```

1. Evaluate model

```sh
docker-compose rm -rm app python cli.py evaluate -c configs/v2-1.yaml
```

1. Register trained model to `ensemble.yaml`
