# install
> sudo dnf install policycoreutils-sandbox

# set
> setenforce 0
> getenforce
  ---> Permissive

# use
> sandbox -X -t sandbox_net -t sandbox_web_t -w 1280x1024 firefox
