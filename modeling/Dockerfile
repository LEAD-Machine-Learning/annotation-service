FROM python:3.8-slim

WORKDIR /annotation_service_modeling

RUN apt-get update && apt-get install -y build-essential
RUN apt-get install ffmpeg libsm6 libxext6 clang gcc -y
RUN apt-get install -y git
RUN apt-get install -y libpq-dev postgresql-server-dev-all

COPY requirements.txt /annotation_service_modeling
RUN pip install --upgrade pip
RUN pip install torch==1.8.0 opencv-python
RUN MACOSX_DEPLOYMENT_TARGET=12.0 CC=clang CXX=clang++ pip install git+https://github.com/pytorch/vision@v0.9.1
RUN GRPC_PYTHON_BUILD_SYSTEM_ZLIB=1 GRPC_PYTHON_BUILD_SYSTEM_OPENSSL=1 pip install av grpcio
RUN pip install -r requirements.txt
RUN pip install git+https://github.com/facebookresearch/detectron2.git
RUN pip install psycopg2
RUN pip install label-studio==1.0.2.post0 label-studio-ml-backend
#RUN pip install git+https://github.com/heartexlabs/label-studio-ml-backend@bd71350670cb794e658a437f11948324ee90b6e7

COPY tools /annotation_service_modeling/tools

EXPOSE 9090