{%- if cookiecutter.use_nvidia_docker == 'yes' -%}
FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04

RUN apt-get update && apt-get install -y \
  git \
  python{{cookiecutter.python_version}} \
  python3-pip \
  python{{cookiecutter.python_version}}-dev \
  libhdf5-serial-dev \
  libhdf5-dev
{%- else -%}
FROM python:{{cookiecutter.python_version}}

RUN apt-get update && apt-get install -y \
  git \
  libhdf5-serial-dev \
  libhdf5-dev
{%- endif %}

RUN pip3 install --upgrade pip

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

ARG UID
ENV PATH $PATH:/home/docker/.local/bin
RUN useradd docker -l -u $UID -s /bin/bash -m
USER docker
