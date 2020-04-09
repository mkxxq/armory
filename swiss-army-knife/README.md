## arguments

#### HTTPS_PROXY 
提供代理供build时使用

## build

#### command

```bash
# build with https proxy
$ docker build . -t jupyter:3.8 --build-arg HTTPS_PROXY={http proxy}

# default
$ docker build . -t jupyter:3.8
```