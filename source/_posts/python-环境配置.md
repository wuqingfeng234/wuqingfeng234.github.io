---
title: python 环境配置
date: 2025-03-25 11:58:12
tags:
---
1、常用国内源
```
pypi 清华大学源：https://pypi.tuna.tsinghua.edu.cn/simple
pypi 豆瓣源 ：http://pypi.douban.com/simple/
pypi 腾讯源：http://mirrors.cloud.tencent.com/pypi/simple
pypi 阿里源：https://mirrors.aliyun.com/pypi
```
2、临时使用国内源
```shell
pip install -e . -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install -i http://mirrors.cloud.tencent.com/pypi/simple  --trusted-host mirrors.cloud.tencent.com flask
```
3、全局使用国内源
```shell
pip config set global.index-url http://mirrors.cloud.tencent.com/pypi/simple
pip config set global.trusted-host mirrors.cloud.tencent.com
pip config list
```
命令运行完成后，pip.conf中内容为：
```conf
[global]
index-url = http://mirrors.tencentyun.com/pypi/simple
trusted-host = mirrors.tencentyun.com
```
```shell
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set global.trusted-host pypi.tuna.tsinghua.edu.cn
pip config list
```
使用python指令创建虚拟环境
```shell
#创建虚拟环境
python3.10 -m venv <your-virtual-environment-name>
#激活虚拟环境
source <your-virtual-environment-name>/bin/activate
```
conda环境配置
```shell
#设置基础环境是否自动激活
conda config --set auto_activate_base false
conda config --set auto_activate_base false
#手动激活基础环境
conda activate base
#创建环境
conda create -n ml python=3.7
#手动激活新创建环境
conda activate ml
#删除环境
conda remove -n ml --all
```
jupyter环境配置
```shell
jupyter kernelspec remove ml
conda install ipykernel
python -m ipykernel install --user --name=ml --display-name "ml"
jupyter kernelspec list
```

4、pip config命令
```shell
pip config --help

Usage:
  pip config [<file-option>] list
  pip config [<file-option>] [--editor <editor-path>] edit

  pip config [<file-option>] get name
  pip config [<file-option>] set name value
  pip config [<file-option>] unset name


Description:
  Manage local and global configuration.

      Subcommands:

          list: List the active configuration (or from the file specified)
          edit: Edit the configuration file in an editor
          get: Get the value associated with name
          set: Set the name=value
          unset: Unset the value associated with name

      If none of --user, --global and --site are passed, a virtual
      environment configuration file is used if one is active and the file
      exists. Otherwise, all modifications happen on the to the user file by
      default.

Config Options:
  --editor <editor>           Editor to use to edit the file. Uses VISUAL or EDITOR environment variables if not
                              provided.
  --global                    Use the system-wide configuration file only
  --user                      Use the user configuration file only
  --site                      Use the current environment configuration file only

General Options:
  -h, --help                  Show help.
  --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to
                              WARNING, ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
  --retries <retries>         Maximum number of retries each connection should attempt (default 5 times).
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup,
                              (a)bort.
  --trusted-host <hostname>   Mark this host or host:port pair as trusted, even though it does not have valid or any
                              HTTPS.
  --cert <path>               Path to alternate CA bundle.
  --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the
                              certificate in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine whether a new version of pip is available for
                              download. Implied with --no-index.
  --no-color                  Suppress colored output
  --no-python-version-warning
                              Silence deprecation warnings for upcoming unsupported Pythons.
```
