# systemd-puma-unit
Systemd unit for Puma web server

## Usage

### Create wrapper script for pumactl

Go to your app directory and run:

```
rvm wrapper RUBYVERSION@GEMSET APPNAME pumactl
```
This will generate a wrapper that can be referenced in unit file:

```
/home/rubyworker/.rvm/bin/APPNAME_pumactl
```

### Setup & using systemd

#### Copy and edit systemd unit file

Copy systemd unit file to /etc/systemd/system and edit unit file. You must setup your:
  - path to wrapper;
  - app directory path;
  - path to puma config;
  - user for run puma.

After installing or making changes to puma.service run:
```
systemctl daemon-reload
```

#### Enable Puma service & add to autostart with system

##### Enable so it starts on boot
```
systemctl enable puma.service
```

##### Initial start up.
```
systemctl start puma.service
```

##### Check status
```
systemctl status puma.service
```

##### Restart
A normal restart. Warning: listeners sockets will be closed while a new puma process initializes.
```
systemctl restart puma.service
```


## Useful links

  1. Official Puma docs for using systemd (not for using with RVM) https://github.com/puma/puma/blob/master/docs/systemd.md
  2. Official example of Puma config file https://github.com/puma/puma/blob/master/examples/config.rb

## Addition for Sidekiq

```
rvm wrapper RUBYVERSION@GEMSET APPNAME sidekiq
```
