# Go-Import-Redirector

Go-Import-Redirector is a dynamic http server to handle `go get` vanity URLs.

# OpenRC Setup
1. Install the init script into `/etc/init.d/go-import-redirector`
2. Symlink it to `/etc/init.d/go-import-redirector:$port` where port >= 1024, this will be the listen port.
3. Install the configuration file into `/etc/conf.d/go-import-redirector:$port` and edit it appropriately.
4. Start the service

You can omit the `:$port` bits if you set `addr` in the configuration file.
Otherwise, it will default to port `80` (which will fail due to lack of permissions).
If you want that, you can use setcap (`setcap 'cap_net_bind_service+=ep' go-import-redirector`) to allow the executable to bind to port 80.
