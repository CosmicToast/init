# Pleroma

Pleroma is a relatively lightweight ActivityPub implementation.

# OpenRC Setup
1. Install the init script into /etc/init.d/pleroma
2. Create a system group and user "pleroma"
3. Install pleroma OTP edition into /opt/pleroma
4. Configure pleroma as per OTP documentation - the service doesn't care about any of that
5. Start the service

Note that `curl` being present on the `$PATH` is currently required for healthchecks to function.

Possible expansions:
* You can set the `directory` variable in `/etc/conf.d/pleroma` to change the location to which you install the OTP release.
* You can set the `health_host` variable in the `conf.d` file to enable healthchecks, it should be present to the host+port that pleroma is listening on.

TODO: special command to update pleroma (including automatic migrations).

An example `conf.d` file can be found in this repository.
However, do note that it is *not* required for proper functioning.
It is most useful if you want to enable openrc healthchecks.
