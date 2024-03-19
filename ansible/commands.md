# ansible-config
## view
> ansible-config view
print the contents of the current effective Ansible configuration
## dump
> ansible-config dump
print the effective settings, which are made up from explicit settings from the 
effective files and the default settings where an option is unset
> ansible-config dump --only-changed
## list
> ansible-config list
this fully details the settings that can be made, either through variables or
via directives in the configjthis file or Playbook
> ansible-config list | grep -A DEFAULT_REMOTE_USER


