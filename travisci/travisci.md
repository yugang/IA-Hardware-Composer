#Travis CI Docker

=Ubuntu 16.04 LTS) with "su root"=
Refer to https://docs.travis-ci.com/user/common-build-problems/#Running-a-Container-Based-Docker-Image-Locally

* Install Docker: apt-get install docker
* Download Travis CI Docker image(refer to https://hub.docker.com/u/travisci/): docker pull travisci/ci-garnet:packer-1490989530
* Start Docket service: service docker start
* List existing images: docker images
* Don't use this vritual net interface as we only need use --net=host: ifconfig docker0 down
* Run Travis CI image in Docker: docker run --name travis-debug-001 --rm -v /mnt:/mnt/  --net=host -dit travisci/ci-garnet:packer-1490989530 /sbin/init
* Switch to shell: docker exec -it travis-debug-001 bash -l
* Setup network, e.g. proxy....to install dependance packages
* Save changed image to new name: docker commit travis-debug-001 travis-debug-002
