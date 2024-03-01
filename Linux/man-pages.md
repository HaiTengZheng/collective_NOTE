# install man pages
> sudo dnf install man-pages
> dnf install man man-db

# posix man pages
it is non-free, belong to the IEEE
POSIX 头文件手册是手册的一个特殊部分
对于 fedora 这部分称为 0p
## first: enable thirty part software repositories
enable nonfree repository
```bash
sudo dnf install \
  https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
## then: install posix pages
> sudo dnf install man-pages-posix

# install c++ man pages
> dnf install libstdc++-docs

