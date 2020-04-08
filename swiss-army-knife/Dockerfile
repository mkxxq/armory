FROM python:3.8-slim
# change mirror
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's/ftp.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's|security.debian.org/debian-security|mirrors.ustc.edu.cn/debian-security|g' /etc/apt/sources.list 
RUN apt update \
    && apt install -y  --no-install-recommends git curl python python-dev

RUN mkdir ~/.pip && echo "[global]\nindex-url = https://mirrors.aliyun.com/pypi/simple/\n[install]\ntrusted-host=mirrors.aliyun.com\n" >> ~/.pip/pip.conf

# setup jupyter 
RUN pip3 install jupyter --no-cache-dir 

# setup python2 kernel
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python2 get-pip.py
RUN pip2 install ipykernel
RUN python2 -m ipykernel install --user

RUN mkdir /notebooks
WORKDIR /notebooks

# start
EXPOSE 8888
CMD jupyter notebook --ip 0.0.0.0 --port 8888 --no-browser --allow-root



