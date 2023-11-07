# service units
> the equivalent of init scripts on old Sys V systems

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# [Unit]
contains parameters that can be placed in any type of unit file
> man systemd.unit
## Description=
- tell the human user that the service is
- `systemctl status` pulls its description information from this line
## After=
don't start until other things have happed
## Documentation=
shows where to find the Documentation
## CondionPathExists=
checks for either the existence or non-existence of a file
- CondionPathExists=!...
`!` means non-existence

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# [Service]
contains parameters that can only be placed in a service unit file
> man systemd.service
## Type=
- forking 

the traditional behavior for Unix services:
    When the parent process exits, the sytemd service manager will finally
        recognize the service as having fully started

- notify 
the service will send a notification message when the service has finished
    starting, after it sends the notification message, systemd will continue
    loading the follow-up units
## Environment=
sets an environment variable that affects the behavior of the service
## EnvironmentFile=
cases systemd to read a list of environmental variables from the specified file
- =-
`-` sign in front of the path to the file tells systemd that if the file
    doesn't exist, don't worry about it and start the service anyway
## ExecStartPre=
tells systemd to run a specified command before it starts the services with
    `ExecStart` parameters
## ExecStart=, ExecStop=, ExecReload=
points the way to the executable files, and specify the command arguments for
    starting, stopping, and reloading the service
## PrivateTmp=
- True
when set to true, force to write its temporary files to a private `/tmp/`
    directory that nobody else can access
## Restart=
- on-abort
if service were to crash with an unclean signal, systemd would automatically
    restart it
- on-failure
restart because of an unclean exit code, a timeout, or a watchdog event
    (watchdog: a kernel feature that can restart a service upon some sort
    of unrecoverable error)
## RestartPreventExitStatus=
prevents the service from automatically restarting if a certain exit code is
    received
> man systemd.exec  ($EXIT_CODE, $EXIT_STATUS_ section)
## KillMode=
> man systemd.kill
the behavior when send a kill signal to it 
- process
a kill signal will only kill the main process for the service, all other
    associated process will remain running
## RuntimeDirectory= and RuntimeDirectoryMode=
create runtime directory under the `/run/` directory, and then set the
    permissions value for that directory


-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# [Install]
## WantedBy=
control what happens when you enable or diable a unit
- multi-user.target
we want the service to be enable for the multi-user.target unit, which will
    cause the service to automatically start when the machine boots into the
    multi-user target (the multi-user target is when the machine is fully
    booted and ready for use, same as `runlevel` in SysV)
## Alias=
control the service by specifying either name


