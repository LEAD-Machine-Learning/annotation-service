FROM python:3.8-slim

WORKDIR /annotation_service_labeling

RUN apt-get update && apt-get install -y build-essential
RUN apt-get install ffmpeg libsm6 libxext6 -y
RUN apt-get install -y git

COPY requirements.txt /annotation_service_labeling
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN pip install psycopg2-binary
RUN pip install label-studio==1.0.2.post0

COPY configs /annotation_service_labeling/configs

EXPOSE 8080