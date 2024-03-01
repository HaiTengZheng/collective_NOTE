# nmcli
NetworkManager command-line interface
> nmcli [options] OBJECT { COMMAND | help }

# overview
## get the connection overview
> nmcli -o connection
## get the overshow of device (e.g. wlp1s0)
> nmcli -o dev show wlp1s0


# list the `keyfiles` of network connections
> nmcli -f TYPE,FILENAME,NAME connection

# list the available Wi-Fi access points
no more that 30 seconds old by enabling a network scan if necessary
> nmcli dev wifi list
color represent signal
cyan    : a weak signal (less than 30% intensity)
magenta : a stronger signal (30 - 50%)
orange  : a better signal (60 - 80%)
green   : an excellent signal (80 - 100%)
## --rescan
the scan could be forced to be disable, regradless of the age of the access 
point list

# list device
> nmcli device
## list wifi device
> nmcli dev wifi list

# connect wifi
> nmcli device wifi connect [SSID] password [SSID-password]
