## Jupyter ROCm for Jupyterhub with tensorflow-rocm inside
-----

#### Pull image
```
docker pull izone/jupyter:rocm3.5-tf2.2.0-python37
```
#### Run
```
docker run --rm --name Jupyter-rocm \
--device=/dev/kfd \
--device=/dev/dri \
-ti izone/jupyter:rocm3.5-tf2.2.0-python37
```

-----
#### Build
```
docker build -t izone/jupyter:base-notebook-python37 ./base-notebook-python37/
```
```
docker build -t izone/jupyter:rocm3.1-tf2.1.1-python37 -f ./Dockerfile.rocm31tf211 .
```
```
docker build -t izone/jupyter:rocm3.5-tf2.2.0-python37 -f ./Dockerfile.rocm35tf220 .
```
```
docker build -t izone/jupyter:rocm3.7-tf2.3.3-python37 -f ./Dockerfile.rocm37tf233 .
```
