## run yarn with production flag
## [Dockerfile](Dockerfile)

```
$ docker build -t 01-yarn-production .
[+] Building 28.2s (13/13) FINISHED
=> [internal] load build definition from Dockerfile                                                                                                                                                                                                                      0.0s
=> => transferring dockerfile: 424B                                                                                                                                                                                                                                      0.0s
=> [internal] load .dockerignore                                                                                                                                                                                                                                         0.0s
=> => transferring context: 81B                                                                                                                                                                                                                                          0.0s
=> [internal] load metadata for docker.io/library/node:18.1.0-bullseye                                                                                                                                                                                                   1.4s
=> [auth] library/node:pull token for registry-1.docker.io                                                                                                                                                                                                               0.0s
=> [1/7] FROM docker.io/library/node:18.1.0-bullseye@sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f                                                                                                                                             0.0s
=> [internal] load build context                                                                                                                                                                                                                                         0.2s
=> => transferring context: 987B                                                                                                                                                                                                                                         0.2s
=> CACHED [2/7] RUN apt update                                                                                                                                                                                                                                           0.0s
=> CACHED [3/7] RUN apt install build-essential                                                                                                                                                                                                                          0.0s
=> CACHED [4/7] WORKDIR /home/node                                                                                                                                                                                                                                       0.0s
=> [5/7] COPY --chown=node:node . .                                                                                                                                                                                                                                      0.0s
=> [6/7] RUN yarn --frozen-lockfile --production                                                                                                                                                                                                                        15.1s
=> [7/7] RUN yarn build                                                                                                                                                                                                                                                  7.2s
=> exporting to image                                                                                                                                                                                                                                                    4.0s
=> => exporting layers                                                                                                                                                                                                                                                   4.0s
=> => writing image sha256:e9de542100d316fba27073bdd412c2cef31e0d08004bfe47d8a16389b3854af7                                                                                                                                                                              0.0s
=> => naming to docker.io/library/01-yarn-production                                                                                                                                                                                                                     0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
$ docker image ls
REPOSITORY           TAG           IMAGE ID       CREATED         SIZE
01-yarn-production   latest        e9de542100d3   9 seconds ago   1.77GB
00-initial           latest        aea2fd476d32   6 minutes ago   1.94GB
```

```
$ docker history 01-yarn-production
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
e9de542100d3   25 seconds ago   CMD ["/bin/sh" "-c" "yarn start"]               0B        buildkit.dockerfile.v0
<missing>      25 seconds ago   RUN /bin/sh -c yarn build # buildkit            7.15MB    buildkit.dockerfile.v0
<missing>      33 seconds ago   RUN /bin/sh -c yarn --frozen-lockfile --prod…   744MB     buildkit.dockerfile.v0
<missing>      48 seconds ago   COPY . . # buildkit                             109kB     buildkit.dockerfile.v0
<missing>      7 minutes ago    WORKDIR /home/node                              0B        buildkit.dockerfile.v0
<missing>      7 minutes ago    USER node                                       0B        buildkit.dockerfile.v0
<missing>      7 minutes ago    RUN /bin/sh -c apt install build-essential #…   1.94MB    buildkit.dockerfile.v0
<missing>      7 minutes ago    RUN /bin/sh -c apt update # buildkit            17.8MB    buildkit.dockerfile.v0
<missing>      4 days ago       /bin/sh -c #(nop)  CMD ["node"]                 0B
<missing>      4 days ago       /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>      4 days ago       /bin/sh -c #(nop) COPY file:4d192565a7220e13…   388B
<missing>      4 days ago       /bin/sh -c set -ex   && for key in     6A010…   7.6MB
<missing>      4 days ago       /bin/sh -c #(nop)  ENV YARN_VERSION=1.22.18     0B
<missing>      4 days ago       /bin/sh -c ARCH= && dpkgArch="$(dpkg --print…   153MB
<missing>      4 days ago       /bin/sh -c #(nop)  ENV NODE_VERSION=18.1.0      0B
<missing>      2 weeks ago      /bin/sh -c groupadd --gid 1000 node   && use…   334kB
<missing>      2 weeks ago      /bin/sh -c set -ex;  apt-get update;  apt-ge…   529MB
<missing>      2 weeks ago      /bin/sh -c apt-get update && apt-get install…   152MB
<missing>      2 weeks ago      /bin/sh -c set -ex;  if ! command -v gpg > /…   19MB
<missing>      2 weeks ago      /bin/sh -c set -eux;  apt-get update;  apt-g…   10.7MB
<missing>      2 weeks ago      /bin/sh -c #(nop)  CMD ["bash"]                 0B
<missing>      2 weeks ago      /bin/sh -c #(nop) ADD file:3a81c181c66f226bd…   124MB
```
