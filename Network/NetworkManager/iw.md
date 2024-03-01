# RSSI (received signal strength indicator)
specifies how strong the received signal is, is measured in `dBm`(decibels
relative to one milliwatt) or 10-3W

# find the RSSI
> /proc/net/wireless
## directly monitor changes in the file
with the `watch` command
> watch -n 1 cat /proc/net/wireless

# iw
iw grabs the information from the /proc/net/wireless file and interprets it
## get the devide link information
> iw wlp1s0 link
