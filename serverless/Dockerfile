FROM public.ecr.aws/amazonlinux/amazonlinux:2.0.20201111.0
LABEL maintainer="Lucas Pearson <lpearson@trek10.com>"

# add nodejs repo
RUN curl --silent --location https://rpm.nodesource.com/setup_14.x | bash -
RUN yum -y install \
  git \
  jq \
  nodejs \
  openssl-devel \
  python27-devel.x86_64 \
  python3 \
  python3-devel \
  gcc \
  zlib-devel

# install pip + aws cli
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py
RUN pip install awscli --upgrade

# update npm to latest version
RUN npm install -g npm

# install serverless framework
RUN npm install -g serverless@2.52.1
