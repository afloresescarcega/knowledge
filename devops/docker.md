

This will list all containers:
```bash
docker container ls --all
```

To remove a container:
```bash
docker rm <container id>
```

Run a Docker container and ceess its shell
```bash
docker container run --interactive --tty --rm ubuntu bash
```
`--interactive` makes the session interactive with a shell
`--tty` makes a pretend-tty
`--rm` removes the container after the program bash exits

Run a Docker container with MySQL container
```bash
docker container run \
--detach \
--name mydb
-e MYSQL_ROOT_PASSWORD=my-secret-pw \
mysql:latest
```
`--detach` runs the contaner in the background
`--name` names the container mydb
`-e` sets an environment variable for mysql 

See what processes are running inside the container
`docker container top mydb`

Run a command inside of a container
```bash
docker exec -it mydb \
  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
```
`-it` Will return display the stdout


Run a new shell process inside of an already-running container
```bash
docker exec -it mydb sh
```

Remember to stop a container before `rm`ing it.
```bash
docker stop <container id>```




