# Notes

## Basics

### Images
- Image is a blueprint of what needs to run application, it'll have the Runtime env (Node or Java), application code, any dependencies, env vars and commands if any.
- Images have their own file system too which is independent of rest of the host machine.
- Images are immutable if we need to bring in changes we will be creating a new version of the image.
- We can now share this image with anyone and they should be able to run application irrespective of the dependency version they are running on their system.

### Container
- Container is a running instance of image
- It is an independent process which runs our application

## Making an Image
### Parent Image
- images are made of different layers and order of these layers matter
- We start with a parent image which includes the OS and the runtime env which we need. ex: Linux with Java 21.
- We will be working with Docker Hub to get these parent images.
- We can download or pull the image using following command
  ```docker pull node```
- We can see the downloaded image in the docker desktop.

### Docker file
- We need to create a file named "Dockerfile" with no extension at root level of project.
- This file tells docker how to create image with all its layers
- The very first (layer) will be the parent image. Using `FROM` command.
- Next we can copy the source code, which will be second layer. `COPY`
- Next we'll need all the dependencies in node it'll be to run `npm install`. This will be our third layer. Using `RUN` command.
- The container will have its own ports, so we'll have to expose the port to host machine this can be donw using `EXPOSE` command. ex: `EXPOSE 4000`.
- Once this is done next we need to supply the command that will be used to run the command. This will be our last layer.  Using `CMD` command

### Build Image
- In order to build the image we run `docker build -t <some-name> .`
- -t will assign a name to this image
- . is the relative path to `Dockerfile`
- This newly created imagw will be visible in docker desktop application
- There can be a few files which we dont want to involve from our source directory such as `node-modules`. For this we'll use `.dockerignore` file (similar .gitignore)