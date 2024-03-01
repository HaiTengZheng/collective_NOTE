# desktop set
> sudo apt-get install tesksel
> tesksel

# switch to test mode as default mode for the current session(until next reboot)
1. > systemctl set-default multi-user.target
/* set our Linux virtual machine to boot to text mode by default */
2. > systemctl isolate multi-user.target
/* re-configure our Linux machine to switch to text mode immediately */
