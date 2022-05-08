# Initial build - aka get it working
## [Dockerfile](Dockerfile)

```
$ docker build -t 00-initial .
[+] Building 60.1s (13/13) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                                                                                                      0.1s
 => => transferring dockerfile: 429B                                                                                                                                                                                                                                      0.0s
 => [internal] load .dockerignore                                                                                                                                                                                                                                         0.1s
 => => transferring context: 2B                                                                                                                                                                                                                                           0.0s
 => [internal] load metadata for docker.io/library/node:18.1.0-bullseye                                                                                                                                                                                                   2.2s
 => [auth] library/node:pull token for registry-1.docker.io                                                                                                                                                                                                               0.0s
 => [1/7] FROM docker.io/library/node:18.1.0-bullseye@sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f                                                                                                                                            20.0s
 => => resolve docker.io/library/node:18.1.0-bullseye@sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f                                                                                                                                             0.0s
 => => sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f 1.21kB / 1.21kB                                                                                                                                                                            0.0s
 => => sha256:73c1ce2540981fec5b9bde1b6738eb08e4e480592afea52b4b8fc3f606b73559 2.21kB / 2.21kB                                                                                                                                                                            0.0s
 => => sha256:c357e2c68cb3bf1e98dcb3eb6ceb16837253db71535921d6993c594588bffe04 10.87MB / 10.87MB                                                                                                                                                                          1.2s
 => => sha256:04232a462409852354778ef0a5be9843f65549711267a25ee3aa005db27b40b7 7.65kB / 7.65kB                                                                                                                                                                            0.0s
 => => sha256:6aefca2dc61dcbcd268b8a9861e552f9cdb69e57242faec64ac120d2355a9c1a 54.94MB / 54.94MB                                                                                                                                                                          3.2s
 => => sha256:967757d5652770cfa81b6cc7577d65e06d336173da116d1fb5b2d349d5d44127 5.16MB / 5.16MB                                                                                                                                                                            0.7s
 => => sha256:c766e27afb21eddf9ab3e4349700ebe697c32a4c6ada6af4f08282277a291a28 54.58MB / 54.58MB                                                                                                                                                                          4.1s
 => => sha256:32a180f5cf85702e7680719c40c39c07972b1176355df5a621de9eb87ad07ce2 196.70MB / 196.70MB                                                                                                                                                                       10.0s
 => => sha256:3507b5066a4044084632b977c7f0e6ddb8641aa1209108b4e03ea05c24d9cc4e 4.20kB / 4.20kB                                                                                                                                                                            3.8s
 => => extracting sha256:6aefca2dc61dcbcd268b8a9861e552f9cdb69e57242faec64ac120d2355a9c1a                                                                                                                                                                                 2.4s
 => => sha256:3c68557c340d5573e07d8ce03ac00c16d180e5c808e18fc960552264e9848790 45.02MB / 45.02MB                                                                                                                                                                          6.3s
 => => sha256:925b4ef5803f90e7defd3fff5858057174039488a5c09f2458335e52505d1b7e 2.28MB / 2.28MB                                                                                                                                                                            4.4s
 => => sha256:3c263125b4e46172df8e673146ef96a8cba50552929be828e87b0aa3a386ea71 454B / 454B                                                                                                                                                                                4.6s
 => => extracting sha256:967757d5652770cfa81b6cc7577d65e06d336173da116d1fb5b2d349d5d44127                                                                                                                                                                                 0.2s
 => => extracting sha256:c357e2c68cb3bf1e98dcb3eb6ceb16837253db71535921d6993c594588bffe04                                                                                                                                                                                 0.3s
 => => extracting sha256:c766e27afb21eddf9ab3e4349700ebe697c32a4c6ada6af4f08282277a291a28                                                                                                                                                                                 2.6s
 => => extracting sha256:32a180f5cf85702e7680719c40c39c07972b1176355df5a621de9eb87ad07ce2                                                                                                                                                                                 7.1s
 => => extracting sha256:3507b5066a4044084632b977c7f0e6ddb8641aa1209108b4e03ea05c24d9cc4e                                                                                                                                                                                 0.0s
 => => extracting sha256:3c68557c340d5573e07d8ce03ac00c16d180e5c808e18fc960552264e9848790                                                                                                                                                                                 2.1s
 => => extracting sha256:925b4ef5803f90e7defd3fff5858057174039488a5c09f2458335e52505d1b7e                                                                                                                                                                                 0.1s
 => => extracting sha256:3c263125b4e46172df8e673146ef96a8cba50552929be828e87b0aa3a386ea71                                                                                                                                                                                 0.0s
 => [internal] load build context                                                                                                                                                                                                                                         2.0s
 => => transferring context: 152.53MB                                                                                                                                                                                                                                     2.0s
 => [2/7] RUN apt update                                                                                                                                                                                                                                                  2.7s
 => [3/7] RUN apt install build-essential                                                                                                                                                                                                                                 1.4s
 => [4/7] WORKDIR /home/node                                                                                                                                                                                                                                              0.1s
 => [5/7] COPY --chown=node:node . .                                                                                                                                                                                                                                      1.0s
 => [6/7] RUN yarn --frozen-lockfile                                                                                                                                                                                                                                     18.5s
 => [7/7] RUN yarn build                                                                                                                                                                                                                                                  7.5s
 => exporting to image                                                                                                                                                                                                                                                    4.6s
 => => exporting layers                                                                                                                                                                                                                                                   4.5s
 => => writing image sha256:aea2fd476d320743b5b2c1c27256103629fe69122d859d3b7e135acf5b16e3fc                                                                                                                                                                              0.0s
 => => naming to docker.io/library/00-initial                                                                                                                                                                                                                             0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
$ docker image ls
REPOSITORY   TAG           IMAGE ID       CREATED          SIZE
00-initial   latest        aea2fd476d32   18 seconds ago   1.94GB
```

```
$ docker history 00-initial
IMAGE          CREATED              CREATED BY                                      SIZE      COMMENT
aea2fd476d32   32 seconds ago       CMD ["/bin/sh" "-c" "yarn start"]               0B        buildkit.dockerfile.v0
<missing>      32 seconds ago       RUN /bin/sh -c yarn build # buildkit            7.62MB    buildkit.dockerfile.v0
<missing>      40 seconds ago       RUN /bin/sh -c yarn --frozen-lockfile # buil…   767MB     buildkit.dockerfile.v0
<missing>      58 seconds ago       COPY . . # buildkit                             151MB     buildkit.dockerfile.v0
<missing>      59 seconds ago       WORKDIR /home/node                              0B        buildkit.dockerfile.v0
<missing>      59 seconds ago       USER node                                       0B        buildkit.dockerfile.v0
<missing>      59 seconds ago       RUN /bin/sh -c apt install build-essential #…   1.94MB    buildkit.dockerfile.v0
<missing>      About a minute ago   RUN /bin/sh -c apt update # buildkit            17.8MB    buildkit.dockerfile.v0
<missing>      4 days ago           /bin/sh -c #(nop)  CMD ["node"]                 0B
<missing>      4 days ago           /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>      4 days ago           /bin/sh -c #(nop) COPY file:4d192565a7220e13…   388B
<missing>      4 days ago           /bin/sh -c set -ex   && for key in     6A010…   7.6MB
<missing>      4 days ago           /bin/sh -c #(nop)  ENV YARN_VERSION=1.22.18     0B
<missing>      4 days ago           /bin/sh -c ARCH= && dpkgArch="$(dpkg --print…   153MB
<missing>      4 days ago           /bin/sh -c #(nop)  ENV NODE_VERSION=18.1.0      0B
<missing>      2 weeks ago          /bin/sh -c groupadd --gid 1000 node   && use…   334kB
<missing>      2 weeks ago          /bin/sh -c set -ex;  apt-get update;  apt-ge…   529MB
<missing>      2 weeks ago          /bin/sh -c apt-get update && apt-get install…   152MB
<missing>      2 weeks ago          /bin/sh -c set -ex;  if ! command -v gpg > /…   19MB
<missing>      2 weeks ago          /bin/sh -c set -eux;  apt-get update;  apt-g…   10.7MB
<missing>      2 weeks ago          /bin/sh -c #(nop)  CMD ["bash"]                 0B
<missing>      2 weeks ago          /bin/sh -c #(nop) ADD file:3a81c181c66f226bd…   124MB
```
