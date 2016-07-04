#start docker with interact mode
```bash
docker run -t -i ubuntu /bin/bash
```

#remove all containers
```bash
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

#remove all images
```bash
docker rmi $(docker images -q)
```
# mount a host directory
URL: https://docs.docker.com/userguide/dockervolumes/
```bash
docker run -i -t -v /data/okapi:/home/okapi/data canadatom/okapi-docker-file /bin/bash
```

# stop a container
```
ctrl+d
```

# start a container
## list all containers
```bash
docker ps -a
```

## start the container with id
```bash
docker start [container_id]
```

## attach the container
```bash
docker attach [container_id]
```

## list all containers name and IP
```
docker ps | tail -n +2 | while read -a a; do name=${a[$((${#a[@]}-1))]}; echo -ne "$name\t"; docker inspect $name | grep IPAddress | cut -d \" -f 4; done
```

## list all containers name and gitsha
```
docker ps | tail -n +2 | while read -a a; do name=${a[$((${#a[@]}-1))]}; echo -ne "$name\t"; docker inspect $name | grep sha | cut -d \" -f 4 | awk -F "@" '{print $2}'; done
```

## other
```
- Docker Engine Commands
	docker run
	docker ps
	docker logs
	docker start
	docker stop
	docker rm
	docker rmi
	docker version
	docker <COMMAND> --help
	docker port
	docker top
	docker inspect
	docker images
	docker pull
	docker search
	docker login
	docker attach <RUNNING_CONTAINER>
	docker run --link

- Build New Docker Images
	docker commit -m "<MESSAGE>" -a "<AUTHOR NAME>" <CONTAINER_ID> <USER>/<IMAGE_NAME>:<TAG>
	docker build -t <USER>/<IMAGE_NAME>:<TAG> <PATH_TO_Dockerfile>
	docker tag <IMAGE_ID> <USER>/<IMAGE_NAME>:<NEW_TAG>
	docker images --digests | head
	docker push

- Network
	docker network ls
	docker network create -d bridge <NETWORK_NAME>
	docker run -d --net=<NETWORK_NAME> --name <CONTAINER_NAME> <IMAGE_NAME>
	docker network connect <NETWORK_NAME> <CONTAINER_NAME>
	docker exec -it <CONTAINER_NAME> <COMMAND>
	docker network inspect bridge
	docker network rm
	docker network disconnect

- Manage Data in Containers
	docker run -v <HOST_PATH>:<CONTAINER_PATH>
	docker create -v <CONTAINER_PATH> --name <VOLUME_CONTAINER_NAME> <IMAGE> /bin/true
	docker run -d --volumes-from <VOLUME_CONTAINER_NAME> --name <CONTAINER_NAME> <IMAGE>

	- Backup/Restore Data
		docker run --rm --volumes-from <VOLUME_CONTAINER_NAME> -v $(pwd):/backup <IMAGE> tar cvf /backup/backup.tar /dbdata
		docker run -v /dbdata --name dbstore2 ubuntu /bin/bash
		docker run --rm --volumes-from dbstore2 -v $(pwd):/backup ubuntu bash -c "cd /dbdata && tar xvf /backup/backup.tar --strip 1"
```
