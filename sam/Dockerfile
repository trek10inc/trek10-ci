FROM amazonlinux:with-sources
LABEL maintainer="Jared Short <jshort@trek10.com>"

RUN yum update -y
# add nodejs repo
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -
RUN yum -y install \
  git \
  jq \
  openssl-devel \
  python-devel.x86_64 \
  python3-devel \
  gcc \
  zlib-devel

# install pip + aws cli
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py
RUN pip install awscli --upgrade

# install SAM cli
RUN pip install aws-sam-cli
