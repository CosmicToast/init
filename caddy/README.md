# Caddy

Caddy is a highly convenient webserver that uses TLS by default.

## OpenRC Setup
1. Install the init script into /etc/init.d/caddy
2. Create a system group and user "caddy"
3. Create a file /etc/caddy/Caddyfile - see caddy documentation as to what should go there
4. Start the service

If you are manually installing the executable, don't forget to run `setcap 'cap_net_bind_service+=ep' caddy` on the executable.
Note that `curl` being present on the `$PATH` is currently required for healthchecks to function.

Possible expansions:
* You can symlink `/etc/init.d/caddy` to `/etc/init.d/anything` and the `/etc/anything` directory will be used.
  This allows you to host multiple caddy instances on a single machine (but be careful - only one can manage ports :80, :443 and :2019 at a time).
* All of caddy's data will be held inside `/etc/init.d/caddy/home/{config,data}`.
  This directory will be managed by the init script.
  This way, if you want to back up caddy's state and config at once, you can simply back up `/etc/init.d/caddy`.
* You can set the `directory` variable in `/etc/conf.d/caddy` to override `/etc/anything` to anything you want.
* There is a health check present by default, against localhost:2019.
  You can override where the check goes by setting `healthcheck_location` in the `conf.d` file.
  Explicitly set it to empty (`healthcheck_location=''`) to disable healthchecks.
* By default, the options passed to caddy are `--config /etc/caddy/Caddyfile` (with accounting for alternative directories).
  You can override this by setting `caddy_opts` in the `conf.d` file.
* You can explicitly check whether the current configuratin is valid by using the `checkconfig` additional command (e.g `service caddy checkconfig`).
* You can reload caddy without downtime by using the `reload` additional command.

An example `conf.d` file can be found in this directory.
However, do note that it is *not* required for proper functioning - all-defaults will work fine for most deployments.
