### Dockerfile
To run K.sh with Docker, please make use of the [Dockerfile](https://raw.githubusercontent.com/ctubio/Krypto-trading-bot/master/etc/Dockerfile):

1. Install [docker](https://www.docker.com/) for your system before proceeding. Requires at least Docker 1.7.1. Mac/Windows only: Ensure boot2docker or docker-machine is set up, depending on Docker version. See [the docs](https://docs.docker.com/installation/mac/) for more help.

2. Copy the file [Dockerfile](https://raw.githubusercontent.com/ctubio/Krypto-trading-bot/master/etc/Dockerfile) into a text editor and edit the environment variables (named `API_*`) to match your desired configuration.

3. Save your new Dockerfile, preferably in a secure location and in an empty directory. Then build the images and run the containers:
```
 $ cd path/to/Dockerfile
 $ docker build --no-cache -t ksh .
 $ docker run -p 3000:3000 --name Ksh -t -d ksh
```
If you want to ensure that your data is persisted, mount a local folder into the container's `/data` folder:
```
$ docker run -p 3000:3000 -v /path/to/data:/data --name Ksh -t -d ksh
```

If you run `docker ps`, you should see K container running.

### Vagrantfile
To build your own portable development environment install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and [vagrant](https://www.vagrantup.com/downloads.html), then:
```
 $ cd path/to/K
 $ cp etc/Vagrantfile Vagrantfile
 $ vagrant up
 $ vagrant ssh
```
See more info at [PR #425](https://github.com/ctubio/Krypto-trading-bot/pull/425).

### K.sh.dist
Used on install to initialize `./K.sh` file, feel free to add your own hardcoded arguments to your own `./K.sh` file after install.

### ../src/bin/trading-bot/www/.bomb.gzip
Used by `--whitelist` argument to attempt to crash UI clients from alien IPs not whitelisted; no need to open.
