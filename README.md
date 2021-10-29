## Tensorflow ROCm and NVIDIA for Jupyterhub 
-----

#### Pull image
```
docker pull izone/jupyter:rocm3.5-tf2.2.0-python37
```

-----
## Running

#### ROCm
```
docker run --rm --name Jupyter-rocm \
--device=/dev/kfd \
--device=/dev/dri \
-ti izone/jupyter:rocm3.5-tf2.2.0-python37
```
#### NVIDIA
```
docker run --gpus all -it --rm izone/jupyter:nvidia-tensorflow \
python -c "import tensorflow as tf; print('Num GPUs Available: ', len(tf.config.list_physical_devices('GPU')))"
```
```
docker run --gpus all -it --rm izone/jupyter:nvidia-tensorflow \
python -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```
```
docker run --rm --gpus all --name TensorFlow \
-p 8888:8888 \
-v $HOME/notebooks:/root/notebooks \
-u root \
-ti izone/jupyter:nvidia-tensorflow \
jupyter notebook \
	--allow-root \
	--no-browser \
	--ip=0.0.0.0 \
	--port=8888 \
	--notebook-dir=/root/notebooks \
	--NotebookApp.token=''
```

-----
## Builds

#### ROCm
```
docker build -t izone/jupyter:rocm3.1-tf2.1.1-python37 -f ./Dockerfile.rocm31tf211 .
```
```
docker build -t izone/jupyter:rocm3.5-tf2.2.0-python37 -f ./Dockerfile.rocm35tf220 .
```
```
docker build -t izone/jupyter:rocm3.7-tf2.3.3-python37 -f ./Dockerfile.rocm37tf233 .
```

#### NVIDIA
```
docker build -t izone/jupyter:cuda11.2-tf2.6.0-python39 -f ./Dockerfile.cuda112tf260 . 
```
