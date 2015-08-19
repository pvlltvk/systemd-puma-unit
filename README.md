# systemd-puma-unit
Systemd unit for Puma web server

## Usage

1. ### Create wrapper script for pumactl

Go to your app directory and run:

```
rvm wrapper RUBYVERSION@GEMSET app_name pumactl
```
This will generate a wrapper that can be referenced in unit file:

```
/home/rubyworker/.rvm/bin/app_name_pumactl
```

2. ### Copy and edit systemd unit file

Copy systemd unit file to /etc/systemd/system and edit unit file (change paths to wrapper and app directory)

3. ### Enable puma.service

Run:

```
 systemctl enable puma.service
```