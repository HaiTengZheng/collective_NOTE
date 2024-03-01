# systemd-logind
the tight integration between `systemd` and `cgroups`
> man systemd-logind
> /lib/systemd/system/systemd-logind.service

## systemd-logind.service
```bash
Wants=user.slice
# with cgroups, a user slice must be created for every user who logs in
After=nss-user-lookup.target
# Name service Switch (NSS), determines where the system is look for various 
# types of information, including user authentication information.
# config location: /etc/nsswitch.conf
```

## /etc/nsswitch.conf
- sss:  User and group information will be pulled from the 
        System Security Services Daemon (SSSD).
        user authentication means : LDAP, FreeIPA, Microsoft Active Directory, 
        if don't use any, pull from : `/etc/passwd`, `/etc/group`, `/etc/shadow`,
        `/etc/gshadow`

## /etc/systemd/logind.conf
the configuration file for `systemd-logind.service`
> man logind.conf
### don't keep user's processes going after he logs out
KillOnlyUsers=username
### power management directives
HandlePowerKey=
HandleSuspendKey=
HandleHibernateKey=
HandleLidSwitch=
HandleLidSwithExternalPower=
HandleLidSwitchDocked=

# loginctl
a management utility
- session:  A session gets created whenever a user logs into the system. Each
            session is assigned a decimal number as its ID.
- seats:    A seat consists of all of hardware that is assigned to a specific
            workstation. Each seat has an assigned text-string name that consists
            of from 1 to 255 characters. A user who logs into a computer at at
            the local console will always be assigned a seat. User who log in 
            remotely will not be assigned a seat.
            Creating new seats involoves configuring `udev` rules
> loginctl list-sessions
> loginctl user-status username
> loginctl session-status session_number
> loginctl terminate-session session_number
> loginctl terminate-user username

# PolicyKit and polkit
They aren't part of the systemd ecosystem, but `systemd-logind` does provide
access to polkit functionality.
- It allows a normally non-privileged user to perform certain privileged tasks.
- polkit comes pre-configured with a set of administrative tasks for which it
  can grant root privileged.
> /etc/polkit-1/rules.d/
> man 8 polkit
The big difference: on red-hat, members of the whell group have full sudo 
privileged
> /usr/share/polkit-1/actions/
