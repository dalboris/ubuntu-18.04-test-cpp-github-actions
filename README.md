This repository is a test of a Docker image for building C++ projects on
Ubuntu 18.04 with GitHub Actions

See: https://github.com/dalboris/test-cpp-github-actions

How to build and publish the Docker image for use in GitHub actions?

1. Create an account on Docker Hub

2. Install Docker on your machine, see: https://docs.docker.com/get-docker/

3. (Optional but recommended) Configure the Docker's credentials store for
   more secure login to Docker Hub. See: https://docs.docker.com/engine/reference/commandline/login/#credentials-store

   If you're on Ubuntu, you can for example do something like this:

   a. `sudo apt install gnupg pass`
   
   b. `gpg --full-generate-key` (When prompted: RSA and RSA, 4096, Your Name <yourname@example.com>)

   c. Download `docker-credential-pass-v0.7.0.linux.amd64` from https://github.com/docker/docker-credential-helpers/releases , make it executable, and add it to your PATH

   d. Add the line `"credsStore": "pass-v0.7.0.linux-amd64"` to your `~/.docker/config.json`

5. `docker build -t ubuntu-18.04-test-cpp-github-actions .`

6. `docker login -u yourname`

7. `docker tag ubuntu-18.04-test-cpp-github-actions yourname/ubuntu-18.04-test-cpp-github-actions`

8. `docker push yourname/ubuntu-18.04-test-cpp-github-actions`


Each time you make an update to the Dockerfile, you need to do the following to update it on Docker Hub:

```
docker tag ubuntu-18.04-test-cpp-github-actions yourname/ubuntu-18.04-test-cpp-github-actions
docker push yourname/ubuntu-18.04-test-cpp-github-actions
```

You can see that the SHA256 of the image should be updated on Docker Hub.
