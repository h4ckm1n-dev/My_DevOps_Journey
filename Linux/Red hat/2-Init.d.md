Init.d is the traditional SysV init system used in older versions of Linux distributions. It has been largely replaced by systemd, but some legacy systems may still use init.d. Here's a cheat sheet for init.d commands:

## Service Management

|COMMAND|DESCRIPTION|
|---|---|
|`service <service> start`|Start a service|
|`service <service> stop`|Stop a service|
|`service <service> restart`|Restart a service|
|`service <service> reload`|Reload the configuration of a service|
|`chkconfig <service> on`|Enable a service to start on boot|
|`chkconfig <service> off`|Disable a service from starting on boot|
|`service <service> status`|Check the status of a service|

## System Control

|COMMAND|DESCRIPTION|
|---|---|
|`shutdown -h now`|Shut down the system|
|`reboot`|Reboot the system|

Note: The init.d system doesn't have direct commands for suspend or hibernate. These functionalities may vary depending on the specific Linux distribution and desktop environment being used.

Please keep in mind that init.d is considered a legacy system, and it's recommended to use systemd whenever possible, as it provides more advanced features and better compatibility with modern Linux distributions.