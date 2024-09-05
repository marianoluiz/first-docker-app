# coding-project-template

cd CC201/labs/1_ContainersAndDocker/

list all image
- docker images

pull image
- docker pull hello-world

check again all image
- docker images

run image as container
- docker run hello-world

List the containers to see that your container ran and exited successfully.
- docker ps -a

Remove container at device:
- docker container rm <container_id>

check again
- docker ps -a

The docker images command lists all Docker images that are available on your local machine, not just those in a specific repository. It shows images that have been pulled from Docker Hub or other registries, as well as images that you have built locally.

Remove a Container:
- docker rm <container_id_or_name>

Remove an Image:
- docker rmi <image_id>

build the image:
- docker build . -t myimage:v1

    Breakdown of the Command
    docker build:

    This is the Docker command used to build an image from a Dockerfile.
    . (dot):

    The dot represents the build context, which is the current directory. Docker will look for a Dockerfile in this directory and use the files in this directory as the context for the build.
    -t myimage:v1:

    The -t flag is used to tag the image with a name and optionally a tag in the name:tag format.
    myimage is the name of the image.
    v1 is the tag for the image. Tags are useful for versioning your images.

run docker: 
- docker run -dp 8080:8080 myimage:v1

    docker run:
    This is the Docker command used to create and start a new container from a specified image.
    -d:

    The -d flag stands for "detached mode". It runs the container in the background and prints the container ID. This allows you to continue using the terminal while the container runs in the background.
    -p 8080:8080:

    The -p flag is used to publish a container’s port(s) to the host.
    8080:8080 maps port 8080 on the host to port 8080 on the container. This means that any traffic sent to port 8080 on the host will be forwarded to port 8080 on the container.
    myimage:v1:

    This specifies the image to use for the container. In this case, it uses the image named myimage with the tag v1.

see output in terminal: 
- curl localhost:8080

stop docker:
- docker stop $(docker ps -q)

  docker ps -q to pass in the list of all running containers
  You can specify ID of container after stop


check if container stopped:
- docker ps

(Need login)

Push the image to IBM Cloud Container Registry:
ibmcloud target

ibmcloud cr namespaces

ibmcloud cr region-set us-south

ibmcloud cr login

export MY_NAMESPACE=sn-labs-$USERNAME

docker tag myimage:v1 us.icr.io/$MY_NAMESPACE/hello-world:1

docker push us.icr.io/$MY_NAMESPACE/hello-world:1

ibmcloud cr images

ibmcloud cr images --restrict $MY_NAMESPACE

https://cf-courses-data.static.labs.skills.network/cc201/labs/1_ContainersAndDocker/instructions.md.html