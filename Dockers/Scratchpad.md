# Notes

## Basics

### Images
- Image is a blueprint of what needs to run, it'll have the Runtime env (Node or Java), application code, any dependencies, env vars and commands if any.
- Images have their own file system too which is independent of rest of the host machine.
- Images are immutable if we need to bring in changes we will be creating a new version of the image
