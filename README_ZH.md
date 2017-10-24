# zinaer-skm

Zinaer SKM 是一个简洁，强大的 SSH 密钥管理工具。让你能够轻松管理大量的 SSH 密钥。

其它语言：

* [English](https://github.com/zinaer/zinaer-skm/blob/master/README.md)

![](https://github.com/zinaer/zinaer-skm/blob/master/zinaer_skm.gif)

### 特性

* 创建，查看和删除你的 SSH 密钥
* 通过别名管理你所有的 SSH 密钥
* 选择并设置默认的 SSH 密钥
* 备份和回复你所有的 SSH 密钥

### 安装

#### Mac OS X

```
sudo curl https://github.com/zinaer/zinaer-skm/blob/master/mac/skm -O /usr/local/bin/
``` 

#### Linux

```
sudo curl https://github.com/zinaer/zinaer-skm/blob/master/linux/skm -O /usr/local/bin/
```

### 使用

```
$ skm

usage: skm [-h] [-v] [-i [init]] [-c [create]] [-l [ls]] [-u [use]]
           [-d [delete]] [-b [backup]] [-r [restore]]

Zinaer SKM - Manage your multiple SSH keys easily.
--------------------------------------------------
    Author: zinaer.com
    Website: https://skm.zinaer.com
    Version: 1.0

optional arguments:
  -h, --help     show this help message and exit
  -v, --version  print the version
  -i [init]      Initialize SSH keys store for the first time use
  -c [create]    Create a new SSH key
  -l [ls]        List all the available SSH keys
  -u [use]       Set specific SSH key as default by its alias name
  -d [delete]    Delete specific SSH key by alias name
  -b [backup]    Backup all SSH keys to an archive file
  -r [restore]   Restore SSH keys from an existing archive file

Please enjoy it!
```

#### 第一次使用

第一次使用先进行初始化 SSH 密钥的存储。

```
$ skm -i
✔ SSH key store initialized!
Key store location is: /Users/zinaer/.skm/
```

Zinaer SKM 将创建目录 `$HOME/.skm` 存储所有的 SSH 密钥。

**说明：**如果你在 `$HOME/.ssh` 目录已经有 id_rsa 和 id_rsa.pub 密钥，Zinaer SKM 会移动它们到 `$HOME/.skm/default` 目录。

#### 创建一对新的 SSH 密钥

**说明：**当前只支持 RSA 密钥类型。

```
$ skm -c zinaer

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Generating public/private rsa key pair.
Your identification has been saved in /Users/zinaer/.skm/zinaer/id_rsa.
Your public key has been saved in /Users/zinaer/.skm/zinaer/id_rsa.pub.
The key fingerprint is:
...
✔ SSH key [zinaer] created!
```

#### 查看所有的 SSH 密钥

```
$ skm -l

✔ Found 2 SSH key(s)!

default ✔
zinaer
```

#### 设置默认使用的 SSH 密钥

```
$ skm -u zinaer
Now using SSH key: zinaer
```

#### 删除 SSH 密钥

```
$ skm -d zinaer

SSH key [zinaer] is currently in use, please confirm to delete it [y/n]:y
✔ SSH key [zinaer] deleted!
```

#### 备份密钥

备份 `$HOME` 目录下所有的 SSH 密钥。

```
$ skm -b

a .
a ./default
a ./default/id_rsa
a ./default/id_rsa.pub

✔  All SSH keys backup to: /Users/zinaer/skm-20171024131446.tar.gz
```

### 恢复密钥

```
$ skm -r ~/skm-20171024131446.tar.gz

x ./
x ./default/
x ./default/id_rsa
x ./default/id_rsa.pub
✔  All SSH keys restored to /Users/zinaer/.skm
```

### 许可证

[MIT 许可证](https://github.com/zinaer/zinaer-skm/blob/master/LICENSE)

