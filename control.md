# control node

## Preparing the control node - detailed
### Update RPi 3 firmware, kernel and packages
- update the firmware and kernel
```bash
sudo rpi-update
```

- update system's package list
```bash
sudo apt update
```

- upgrade all installed packages to their latest versions
```bash
sudo apt full-upgrade -y
```

### Install packages and clone project
- install needed packages
```bash
sudo apt install -y ansible python-argcomplete git sshpass
```

- create `/etc/bash_completion.d` folder for `python-argcomplete`
```bash
sudo mkdir /etc/bash_completion.d
```

- activate `python-argcomplete` and reboot
```bash
sudo activate-global-python-argcomplete
sudo reboot
```

- create `/ext/repo` folder
```bash
sudo mkdir /ext/repo
```

- modify permission of `/ext/repo`
```bash
sudo chmod 0777 /ext/repo
```

- clone project from GitHub to `/ext/repo/project_automation`
```bash
sudo git clone https://github.com/steled/project_automation.git /ext/repo/project_automation
```