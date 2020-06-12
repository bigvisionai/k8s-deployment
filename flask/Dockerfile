# This is the base image we are going build our app
# If this image does'nt exist in the local system, it checks in the trusted docker registry and downloads it
FROM pytorch/pytorch:latest

# Add a new layer that will create a working directory
WORKDIR /app

# Add a new layer to copy the current directory local files to the working directory
COPY . /app

# Add a new layer to set a environment variable stating not to use cuda
ENV NO_CUDA=1

# Add a new layer to install torchvision, flask, gunicorn
RUN pip install torchvision flask gunicorn

# Add a new layer to execute this shell script while creating the container
CMD exec gunicorn --bind 0.0.0.0:5000 deploy:app
