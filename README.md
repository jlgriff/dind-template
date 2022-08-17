# Introduction

This template provides a straightforward framework for running a container inside of another Docker container (DinD).

# Use-Cases

One reason for doing this is to test how a container performs on a virtual machine, abstracted away from the specifics of your local machine. For instance, you can run a parent container with a newer runtime or compiler version, allowing you to verify the application still works as expected before upgrading.

# Instructions

To run a container from your machine inside of another container:

1. Replace the example bind mount source (`./../my-local-app`) in `docker-compose.yml` with the path to whichever local directory you would like to make available inside the parent Docker container.
    - Note: Unix machines allow relative paths to work, but running this on Windows will require absolute paths to the desired directory.
2. Run `docker compose up`.
3. Run `docker exec -it <dind_container_name> sh` to bash into the running container.
4. Inside the container, run `ls` and verify that the `app` volume is available.
5. `cd` into `app` and run the `Dockerfile`.
