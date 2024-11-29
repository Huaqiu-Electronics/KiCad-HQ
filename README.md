# KiCad-HQ
you can check the repo https://gitlab.com/kicad-hq/kicad



# kicad-HQ install

### Windows

The Windows installation package can be downloaded directly using the following link:
https://www.eda.cn/data/kicad-release/kicad-huaqiu-8.0.6-x86_64.exe.zip

### Linux
The Linux version requires Flatpak installation

#### 1，Install flatpak

`sudo apt install flatpak`

#### 2，Map a domain name to a specific IP address

`sudo vim /etc/hosts`

Use vim to go to etc/host and add this line：
`175.6.14.183 kicad.huaqiu.com`

Check whether the connection is successful:
`ping kicad.huaqiu.com`

#### 3，Add a remote kicad repository

`flatpak remote-add --user repo https://kicad.huaqiu.com/kicadhuaqiu`

Check whether the addition succeeds：
`flatpak remote-ls repo`

If GPG verification is reported, go to Step 4. Otherwise, skip it

#### 4，Ignore package unsigned authentication and modify the configuration with the vim editor

`vim ~/.local/share/flatpak/repo/config`

Modify in the file:
`gpg-verify=false`

`flatpak remote-modify --no-gpg-verify repo`

Check whether the addition is successful:
`flatpak remote-ls repo`

#### 5，Install kicad

`flatpak install repo org.kicad.KiCad`

If no dependency is reported, go to the next step "6".

#### 6，Lack of SDK dependency, use domestic flathub mirror warehouse, add remote warehouse first, and then install the missing dependency:

`sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub`

In case of lack org.freedesktop.Sdk/x86_64/23.08：
`flatpak install flathub org.freedesktop.Sdk/x86_64/23.08`

In case of lack org.freedesktop.Sdk//23.08：
`flatpak install flathub org.freedesktop.Sdk//23.08`
