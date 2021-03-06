# Laravel homestead-docker
Create a homestead docker container for your development env. ( files taken from laravel settler: provision.sh (modified) + serve.sh )

### Install docker && docker compose
please refer to these tutorials:
* install docker (https://docs.docker.com/installation/ubuntulinux/)
* install docker compose (fig alternative) (https://docs.docker.com/compose/install/)

### Build the homestead image
```shell
git clone https://github.com/shincoder/homestead-docker.git
cd homestead-docker
docker build -t shincoder/homestead .
```

### Launch your containers
There are only two containers to run. web container ( includes everything except your database ), and mariadb container.
```shell
sudo docker-compose up -d
```
this will build the image, and start it.

### SSH into the container (password: secret):
```shell
ssh -p 2222 homestead@localhost
```

### Add a virtual host
Assuming you mapped your apps folder to ```/apps``` (you can change mappings in the docker-compose.yml file, it's prefered to use absolute paths), you can do:
```shell
cd / && ./serve.sh myapp.dev /apps/myapp/public
```

### Everything should work - enjoy !!!
Our web container starts nginx, php5-fpm, redis, beanstalk. and has gruntjs, gulp, bower.
some relevant port have been added to docker-compose.yml ( livereload standard port, karma server port ), change them if you need to.
