FROM amazonlinux:2017.09-with-sources
LABEL maintainer="Jared Short <jshort@trek10.com>"

RUN yum update -y
# add nodejs repo
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -
RUN yum -y install \
  git \
  jq \
  nodejs \
  openssl-devel \
  python27-devel.x86_64 \
  python36-devel \
  gcc \
  zlib-devel

# install pip + aws cli
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py
RUN pip install awscli --upgrade
RUN pip install aws-sam-cli

# update npm to latest version
RUN npm install -g npm

ADD ./bin/assume-deploy-role.sh /usr/local/bin/assume-deploy-role
ADD ./bin/cfn-wait.sh /usr/local/bin/cfn-wait
