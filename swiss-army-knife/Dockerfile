FROM python:3.8-slim
# change mirror
ARG HTTPS_PROXY
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's/ftp.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's|security.debian.org/debian-security|mirrors.ustc.edu.cn/debian-security|g' /etc/apt/sources.list 
RUN apt update \
    && apt install -y  --no-install-recommends git curl python python-dev build-essential

RUN mkdir ~/.pip && echo "[global]\nindex-url = https://mirrors.aliyun.com/pypi/simple/\n[install]\ntrusted-host=mirrors.aliyun.com\n" >> ~/.pip/pip.conf

# setup jupyter 
RUN pip3 install jupyter --no-cache-dir 

# setup python2 kernel
RUN curl -L https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python2 get-pip.py && rm get-pip.py
RUN pip2 install ipykernel
RUN python2 -m ipykernel install --user

# install go
RUN https_proxy=$HTTPS_PROXY curl -L https://dl.google.com/go/go1.14.linux-amd64.tar.gz -o go1.14.linux-amd64.tar.gz \
    && tar -C tar -C /usr/local/share/ -xzvf go1.14.linux-amd64.tar.gz \
    && rm go1.14.linux-amd64.tar.gz \
    && mkdir /go

# setup go kernel
ENV GOROOT /usr/local/share/go
ENV GOPATH /go
ENV GO111MODULE on
ENV PATH $GOROOT/bin:$GOPATH/bin:$PATH
RUN https_proxy=$HTTPS_PROXY go get -v github.com/gopherdata/gophernotes \
    && mkdir -p ~/.local/share/jupyter/kernels/gophernotes \
    && cd ~/.local/share/jupyter/kernels/gophernotes \
    && cp "$(go env GOPATH)"/pkg/mod/github.com/gopherdata/gophernotes@v0.7.0/kernel/*  "." \
    && sed "s|gophernotes|$(go env GOPATH)/bin/gophernotes|" < kernel.json.in > kernel.json


# start
RUN echo 'export PATH="${GOROOT}/bin:${GOPATH}/bin:${PATH}"' >> /etc/profile
RUN mkdir /notebooks
WORKDIR /notebooks
EXPOSE 8888
CMD jupyter notebook --ip 0.0.0.0 --port 8888 --no-browser --allow-root



