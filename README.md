Testing only. Not suitable for production systems.

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

```
...
```

### How to execute the script

Steps -

1) ssh to the Ubuntu system as 'root'

2) Download the file using `wget`:

```bash
wget https://github.com/0x1stvan/freepbx17_ubuntu2404_testing/raw/master/sng_freepbx_debian_install.sh -O /tmp/sng_freepbx_debian_install.sh
```

3) Execute the script:

```bash
bash /tmp/sng_freepbx_debian_install.sh
```

The installation duration may vary depending on your internet bandwidth and system capacity.

You can find detailed installation logs at `/var/log/pbx/freepbx17-install.log`.
