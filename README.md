# Dockerfile for Python app using Deep Learning models with NVIDIA GPU support
This Dockerfile is used to deploy Python apps that use deep learning models, including those from Hugging Face, and require the use of NVIDIA drivers and other software to utilize the GPU.

## Base Image
The base image used is the CUDA 11.8.0 image on Ubuntu 22.04 from NVIDIA.

## Software Packages
The following software packages are installed via apt-get:

wget
gcc
openssl
libssl-dev
libbz2-dev
libffi-dev
bzip2
build-essential
libsqlite3-dev
libbluetooth-dev
tk-dev
uuid-dev
ffmpeg
libsm6
libxext6
Frontend and PATH
To avoid prompts, the noninteractive frontend is set, and the environment variable is set to include /usr/local/bin in PATH.

## Python
Python is installed from source. The GPG key and version of Python are set using environment variables.

## Runtime Dependencies for Python
Runtime dependencies for Python are installed via apt-get.

## Symlinks
Some useful symlinks that are expected to exist (/usr/local/bin/python and friends) are made.

## PIP and Setuptools
PIP and Setuptools are installed using get-pip.py. Environment variables are set for PIP version, Setuptools version, and Get-Pip URL.

## Working Directory
The working directory is set to /app.

## Copying Files
The current directory contents are copied into the container at /app. This assumes that the Dockerfile is in the same directory as the application code.

 
## Locale
The locale is set to use UTF-8 encoding.

## Environment Variables
The following environment variables are set:

target_phase=SIT for the target deployment phase

TRANSFORMERS_CACHE=/tmp/huggingface/ for the cache directory for Hugging Face Transformers

## Requirements
Python dependencies specified in requirements.txt are installed.

## Entrypoint
The default command to run when the container starts is set to python.

## Build
To build the Docker image, run the following command:

docker build -t image-name .


## Credits
This Dockerfile is based on the work of the Docker community and the NVIDIA team.
