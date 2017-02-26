### Setup Let's Encrypt

0. Make sure that Shotty is accessible from the Internet with the domain name you want to use

1. Copy shotty keys from container to your host system
```
$ docker cp shotty:/home/config/ssl/keys/ /path/to/keys-storage/
```

2. Stop container
```
$ docker stop shotty && docker rm shotty
```

3. Launch container with mounted keys-storage and your domain as a hostname
```
docker run --name shotty -v /path/to/storage:/media/shotty -v /path/to/keys-storage/keys:/home/config/ssl/keys -p 8888:8888 -p 80:80 -p 443:443 -h your-domain.name shotty/main
```

4. Once you see nginx is working _(check in Monit)_, launch keys-update script
```
docker exec -it shotty /home/config/le/update-key your-domain.com
```
