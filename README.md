# zinaer-skm

Zinaer SKM is a simple and powerful SSH Keys Manager. It helps you to manage your multiple SSH keys easily!

**Other languages：**

* [中文简体](https://github.com/zinaer/zinaer-skm/blob/master/README_ZH.md)

### Features

* Create, List, Delete your SSH key(s)
* Mange all your SSH keys by alias names
* Choose and set a default SSH key
* Backup and restore all your SSH keys

![](https://zinaer-file.b0.upaiyun.com/201710/zinaer_skm.gif)

### Installation

#### Mac OS X

```
sudo curl -L https://github.com/zinaer/zinaer-skm/releases/download/V1.0/zinaer-skm-mac64-1.0.tar.gz \
-o /usr/local/bin/zinaer-skm-mac64-1.0.tar.gz && \
cd /usr/local/bin/ && tar -zxvf zinaer-skm-mac64-1.0.tar.gz
``` 

#### Linux

```
sudo curl -L https://github.com/zinaer/zinaer-skm/releases/download/V1.0/zinaer-skm-linux64-1.0.tar.gz \
-o /usr/local/bin/zinaer-skm-linux64-1.0.tar.gz && \
cd /usr/local/bin/ && \tar -zxvf zinaer-skm-linux64-1.0.tar.gz
```

#### Manual Installation

Download it from [releases](https://github.com/zinaer/zinaer-skm/releases) and extact it to `/usr/local/bin` or your PATH directory.

### Usage

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

#### For the first time use

You should initialize the SSH key store for the first time use:

```
$ skm -i

✔ SSH key store initialized!
Key store location is: /Users/zinaer/.skm/
```

Zinaer SKM will create SSH key store at `$HOME/.skm` and put all the SSH keys in it.

**NOTE:** If you already have id_rsa & id_rsa.pub key pairs in `$HOME/.ssh`, SKM will move them to `$HOME/.skm/default`

#### Create a new SSH key

**NOTE:** Currently **ONLY** RSA key type is supported!

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

#### List SSH keys

```
$ skm -l

✔ Found 2 SSH key(s)!

default ✔
zinaer
```

#### Set default SSH key

```
$ skm -u zinaer
Now using SSH key: zinaer
```

#### Delete a SSH key

```
$ skm -d zinaer

SSH key [zinaer] is currently in use, please confirm to delete it [y/n]:y
✔ SSH key [zinaer] deleted!
```

#### Backup SSH keys

Backup all your SSH keys to `$HOME` directory by default.

```
$ skm -b

a .
a ./default
a ./default/id_rsa
a ./default/id_rsa.pub

✔  All SSH keys backup to: /Users/zinaer/skm-20171024131446.tar.gz
```

### Restore SSH keys

```
$ skm -r ~/skm-20171024131446.tar.gz

x ./
x ./default/
x ./default/id_rsa
x ./default/id_rsa.pub
✔  All SSH keys restored to /Users/zinaer/.skm
```

### Licence

[MIT Licence](https://github.com/zinaer/zinaer-skm/blob/master/LICENSE)

