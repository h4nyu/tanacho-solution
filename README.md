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

2. Build environment image

```sh
docker-compose build app
```

3. Setup dataset
```
datasets/
├── evaluation
├── readme
├── sample_submit
├── train
└── train_meta.json
```

4. Enter the app container

```sh
docker-compose rm -rm app bash
```

5. Create extra samples

```sh
python cli.py extend
```

6. Train model

```sh
python cli.py train -c configs/v2-1.yaml
```

9. Evaluate model

```sh
docker-compose rm -rm app python cli.py evaluate -c configs/v2-1.yaml
```

8. Register trained model to `ensemble.yaml`

    a. add config path to `config_paths`.
  
    b. copy trained model from checkpoints to model

