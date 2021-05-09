Toast's Init Scripts
====================

Various convenience init scripts, organized by-service.

## OpenRC
Scripts will be named `$NAME.initd` and `$NAME.confd`.
`$NAME.confd` should generally be optional.
If it isn't, the file will mention this (e.g "this file is required").

These files should go into `/etc/init.d/$NAME` and `/etc/conf.d/$NAME` respectively.
`$NAME` will generally just be the service name.

Some init scripts can be linked to `$NAME.var`.
If you notice `RC_SVCNAME` mentioned it means that functionality is being used/provided.

They should go into `/etc/init.d/$NAME` and `/etc/conf.d/$NAME` respectively.

By default, init scripts only include functionality everyone will want.
This means that by default, the services will run as root.
See the `conf.d` files for customization (including of that).

## Systemd
Scripts will be named `$NAME.service`.
Sometimes, a `$NAME2.timer` may accompany them if appropriate.
All of these should go either in `/etc/systemd/system`, `/etc/systemd/user` or `~/.config/systemd/user` directories (depending). Assume the first unless otherwise specified.
Sometimes, they will use an external configuration file. In this case, it will generally be mentioned.
