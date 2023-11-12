# install
- neofetch
- fish
- neovim
- util-linux-user (for `chsh` command) 
- pip
- pipx      (make sure https_proxy is set)
- poetry    (python virtual env)
- cronie
- cronie-anacron (is subpackage of cronie)
- bat       (replace 'cat')
- lld
- clang
- openssl-devel
- btop
- exa       (replace 'ls')
- alacritty (a OpenGL terminal emulator)
- ripgrep   (replace 'grep)
- buildah   (Podman companion tools)
- skopeo    (Podman companion tools)
- telnet
- qemu
- postgresql-server
- postgresql-contrib
- fira-code-fonts
- jetbrains-mono-fonts
- zathura
- zathura-plugins-all
- lua
- moreutils (errno -L)
- npm
- dotnet-sdk-7.0
- mariadb
- mariadb-server
- phpMyAdmin    (Web gui for mariadb) 
- latexmk
- libstdc++-docs
- ibus-rime
- iftop
- systat    (provide mpstat)
- iotop
- setuptool (setup) 可不装
- VirtualBox    (download from the web)
- redis
- nmap
- dpdk-devel
- dpdk-tools
- tldr  (community-maintained help pages)
- libvirt-devel
- virt-manager
- squid
- xdotool
- texlive
- setools-console   (SELinux)
- policycoreutils   (SELinux)
- vagrant-libvirt
- fzf
- fd-find
- nload
- fontconfig
- java-11-openjdk
- jenkins
- bcc-devel
- bpftool
- libguestfs-tools-c
- libcgroup-tools
- kernel-doc
- stress-ng
- netplan
- kismet
- wavewon
- linssid-ex (dnf copr enable nucleo/linssid)
- texdoc
- texlive-scheme-full
- numactl
- redhat-lsb
- info
- lyx

# group install
> sudo dnf group install --with-optional
`--with-optional` includes the optional packages
- 'C Development Tools and Libraries'
- 'D Development Tools and Libraries'

# remap Caps Lock key to Ctrl
## dconf
- a database that stores important configuration options
- the backend to GSettings which is the system GNOME applications with
    when they need to discover system preferences
## gsetting
- set dconfg key values directly with the `dconf` command
### list-schemas
list all dconf's schemas
e.g.
> gseeting list-schemas | grep ^org.gnome.desktop
`the org.gnome.desktop.input-sources` schema helps define the keyboard layout
### xkb-options
- the key contains optional keyboard overrides
e.g. (remap Caps Lock with dconf)
> dconf write /org/gnome/desktop/iput-sources/xkb-options "['caps:ctrl_modifier']"

# remove libreoffice
> sudo dnf remove libreoffice-calc

# service
> systemctl start sshd.service
> systemctl enable sshd.service
    which is same as (ln -s '/etc/systemd/system/multi-user.target.wants/sshd.service' 
        '/usr/lib/systemd/system/sshd.service')

# pip install
- jupyterlab-vim 
- pynvim
## config pip
> touch .config/pip/pip.conf
```
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com
```
or use '-i' point the mirror address


# pipx install
- poetry
- jupyterlab
- ipython
- ansible           (pipx install --include-deps ansible)
- ansible-core
- argcomplete       (pipx inject ansible argcomplete)
- csvkit
- mycli


# rust install
> curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
> fish_add_path /home/mustang/.cargo/bin

# rustup install
> rustup component add clippy
> rustup component add rustfmt
enable nightly
> rustup toolchain install nightly --allow-downgrade
enable default
> rustup default

# cargo install
- sccache
- cargo-update
- cargo-expand
- cargo-fuzz
- cargo-watch
- cargo-tree
- cargo-tarpaulin       (code coverage)
- cargo-edit
- mini-redis    (for learning)

# flatpak
- podman
- telegram
