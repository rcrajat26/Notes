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
- The very first (layer) will be the parent image.