# thru cli
docker run --rm ubuntu id -a
docker run --rm --user 1000 ubuntu id -a
docker run --rm --user 1000:1000 ubuntu id -a

# thru Dockerfile
## Failure case
$ cat Dockerfile
FROM ubuntu
USER 1000
RUN apt-get update && apt-get install -y tree

$ docker build -t uid .

## Success case
$ cat Dockerfile
FROM ubuntu
RUN apt-get update && apt-get install -y tree
USER 1000

$ docker build -t uid .
## Success case
$ cat Dockerfile
FROM ubuntu
USER 1000:1000

$ docker build -t uid .
$ docker run --rm uid id -a


## Named user

$ cat Dockerfile
FROM ubuntu

RUN groupadd -g 1000 gdemo
RUN useradd -u 1000 -g 1000 -m demo

$ docker build -t uid .
$ docker run --rm uid id -a

