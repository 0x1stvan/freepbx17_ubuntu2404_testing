Testing only. Not suitable for production systems.

This will help you install freepbx17 to ubuntu 24.04 with php version 8.3 with the modification of the original debian installer and some pre-install task.

```
 ______             _____  ______   __
|  ____|           |  __ \|  _ \ \ / /
| |__ _ __ ___  ___| |__) | |_) \ V /
|  __| '__/ _ \/ _ \  ___/|  _ < > <
| |  | | |  __/  __/ |    | |_) / . \
|_|  |_|  \___|\___|_|    |____/_/ \_\
Your Open Source Asterisk PBX GUI Solution
```

### License

[This modules code is licensed as GPLv3+](https://www.gnu.org/licenses/gpl-3.0.txt)

### Tasks to do before running the install script

#### Add gpg keys

```
sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9 6ED0E7B82643E131 F8D2585B8783D481
sudo gpg --export 0E98404D386FA1D9 | sudo tee /etc/apt/trusted.gpg.d/debian-archive-buster-automatic.gpg > /dev/null
sudo gpg --export 6ED0E7B82643E131 | sudo tee /etc/apt/trusted.gpg.d/debian-archive-bullseye-stable.gpg > /dev/null
sudo gpg --export F8D2585B8783D481 | sudo tee /etc/apt/trusted.gpg.d/debian-archive-bullseye-security.gpg > /dev/null
sudo apt update
```

#### Install PHP 8.3 and download ioncube manually

```
sudo apt install php
```

```
cd /usr/local
wget https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz
tar xf ioncube_loaders_lin_x86-64.tar.gz
```

#### Add zend extension to the top of these files
```
nano /etc/php/8.3/cli/php.ini
nano /etc/php/8.3/apache2/php.ini
```

```
zend_extension=/usr/local/ioncube/ioncube_loader_lin_8.3.so
```

##### Example:
```
[PHP]

zend_extension=/usr/local/ioncube/ioncube_loader_lin_8.3.so
```

#### Restart apache2, validate ioncube is loaded
```
service apache2 restart
php -v
```

##### The output should be this:

```
PHP 8.3.6 (cli) (built: Sep 30 2024 15:17:17) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.3.6, Copyright (c) Zend Technologies
    with the ionCube PHP Loader v13.3.1, Copyright (c) 2002-2024, by ionCube Ltd.
    with Zend OPcache v8.3.6, Copyright (c), by Zend Technologies
```

##### You can execute the installer now

### How to execute the script

Steps -

1) ssh to the Ubuntu system as 'root'

2) Download the file using `wget`:

```bash
wget https://github.com/0x1stvan/freepbx17_ubuntu2404_testing/raw/master/sng_freepbx_debian_install.sh -O /tmp/sng_freepbx_debian_install.sh
```

3) Execute the script:

```bash
bash /tmp/sng_freepbx_debian_install.sh --skipversion
```

4) Copy & enable freepbx.ini from the php 8.2 directory
```
cp /etc/php/8.2/mods-available/freepbx.ini /etc/php/8.3/mods-available/freepbx.ini
phpenmod freepbx
service apache2 restart
```

The installation duration may vary depending on your internet bandwidth and system capacity.

You can find detailed installation logs at `/var/log/pbx/freepbx17-install.log`.
