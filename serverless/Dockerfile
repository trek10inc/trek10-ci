FROM amazonlinux:with-sources
LABEL maintainer="Jared Short <jshort@trek10.com>"

RUN yum update -y
# add nodejs repo
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -
RUN yum -y install \
  git \
  jq \
  nodejs \
  openssl-devel \
  python-devel.x86_64 \
  zlib-devel

# install pip + aws cli
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py
RUN pip install awscli --upgrade

# install python 3
RUN amazon-linux-extras install python3

# update npm to latest version
RUN npm install -g npm

# install serverless framework
RUN npm install -g serverless@1.28.0
