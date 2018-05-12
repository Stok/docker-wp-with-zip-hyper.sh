# Hyper.sh deploy for a customised wordpress

To be able to use Duplicator in wordpress, we need to be able to zip. For this, I created a Dockerfile based on wordpress:latest. See https://github.com/Stok/docker-wp-with-zip.git. The resulting image is sitting on my docker-hub account.
Now, to make use of it and deploy to hyper.sh, I need to create a docker-compose.yml file (see https://docs.hyper.sh/hyper/Feature/container/compose.html)

This docker-compose.yml file pulls the customised docker image from docker-hub, and combines it with mariadb and uploads the lot to hyper.sh. In order to run it, insert `<your-docker-hub-username>` (I'm assuming you have a docker-hub account, and that you've uploaded your modified wordpress image. See link above. If you want this exact image, feel free to use mine.), `<your-fip>` (obtained from hyper.sh) and your desired `<sql_root_pw>`. 

For the next part, you'll have to install hyper.sh's CLI. Instructions can be found on their site when you sign up. Then run
```
hyper compose up -d
```
The `-d` is for detach.

To stop:
```
hyper compose down
```

To delete permanently:
```hyper compose down -v ```