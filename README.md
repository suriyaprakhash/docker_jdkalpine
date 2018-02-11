Docker container: JDK Alpine + Demo jar

## Build the image

```sh
docker build -t demo_jdkalpine .
```

## Running the container

```sh
docker run -p 8080:8080 demo_jdkapline
```
here ```8080:8080``` boot2dockerhost:dockercontainerhost, local port forwarding has to be done to access the application in local

## Port forwarding

Host ip - 127.0.0.1 

hostport - 8080 (host machine port)

guestpot - 8080 (boot2docker)

## How to use

```
curl -u suriya http://localhost:8181/demo/start
```
here ```suriya``` is _spring security username_ when prompted type password ```secret```


## Dockerfile

1. Pull jdk alpine
2. Add the currnet jar to the app.jar
3. Set the entrypoint and invoke the jar

If needed the `ARG` can be used get values from cli as `--build-args`
_eg_ 

__Note__ 
1. `COPY` and `ADD` are same .
2. `-Djava.security.egd=file:/dev/./urandom` is set beacuse of the java bug. https://ruleoftech.com/2016/avoiding-jvm-delays-caused-by-random-number-generation

## Useful docker commands

* Build

```sh
docker build -t {tagname} -f {dockerfile} --build-args ORGKEY=orgvalue .
```

* Tag

```sh
docker tag {exisingtagname} {newtagname}
```

* Run

```sh
docker run -p 8080:8080 {image_id/image_name}
```

* Show images

```sh
docker images
docker images -a
```

* Show containers
```sh
docker ps 
docekr ps -a
```

* Push
```sh
docker push {registryhostname/path/app:version}
```

* Pull
```sh
docker pull {registryhostname/path/app:version}
```

* Remove image
```sh
docker rm {imageid}
```
use comma for multiple images
* Remove container
```sh
docker rm {containerid}
```
use comma for multiple containers

* Inspect
```sh
docker exec -it {runningcontainerid} bash
```

* Prune
```sh
docker system prune
docker system prune -a
```