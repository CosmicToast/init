Toast's Init Scripts
====================

I have, at some point, written a "service"-type file for every init system type out there (systemd, upstart, some variant of sysv, openrc and runit, to be specific).
For most of them (systemd, runit, openrc), I try and learn the correct way of "doing things".
As a result, I end up in shock over some... less well-composed scripts distributed with some distributions.
When that happens, I replace them!
This repository will contain various scripts I write/modify from now on.

### Directory Structure

- `init.d`: openrc initscripts
- `conf.d`: openrc default configuration files
- `systemd`: systemd units
- `runit`: runit `./run` files
