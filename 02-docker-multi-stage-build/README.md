## run yarn with production flag
### multi stage
```
$ docker build -t 02-docker-multi-stage-build .
[+] Building 7.4s (8/8) FINISHED
=> [internal] load build definition from Dockerfile                                                                                                                                                                                                                      0.0s
=> => transferring dockerfile: 1.20kB                                                                                                                                                                                                                                    0.0s
=> [internal] load .dockerignore                                                                                                                                                                                                                                         0.0s
=> => transferring context: 48B                                                                                                                                                                                                                                          0.0s
=> [internal] load metadata for docker.io/library/node:16-alpine3.14                                                                                                                                                                                                     1.5s
=> [internal] load build context                                                                                                                                                                                                                                         1.9s
=> => transferring context: 107.07MB                                                                                                                                                                                                                                     1.9s
=> [stage-1 1/3] FROM docker.io/library/node:16-alpine3.14@sha256:53a5c087654e75f8b12475fe143c5ab8b5f33254a37dc87743d066a57e67b4de                                                                                                                                       3.5s
=> => resolve docker.io/library/node:16-alpine3.14@sha256:53a5c087654e75f8b12475fe143c5ab8b5f33254a37dc87743d066a57e67b4de                                                                                                                                               0.0s
=> => sha256:1586b34e36a324dfe04d2f978b6ba900c4591bb3118b8d1d26bcb50189b8ee61 6.58kB / 6.58kB                                                                                                                                                                            0.0s
=> => sha256:8663204ce13b2961da55026a2034abb9e5afaaccf6a9cfb44ad71406dcd07c7b 2.82MB / 2.82MB                                                                                                                                                                            0.3s
=> => sha256:8c392e9e905c179c05811b562acb9e9bb4161e4f967144b8908e744e205c342a 35.54MB / 35.54MB                                                                                                                                                                          1.5s
=> => sha256:36ce72f2f1291c6db07fda7da4445166f00af667ef7d66774188186e26b88068 2.34MB / 2.34MB                                                                                                                                                                            0.8s
=> => sha256:53a5c087654e75f8b12475fe143c5ab8b5f33254a37dc87743d066a57e67b4de 1.43kB / 1.43kB                                                                                                                                                                            0.0s
=> => sha256:8da648aad7e8fd08e4392659e22047145ed9f81ea4c8e00d162b490b05c9a61b 1.16kB / 1.16kB                                                                                                                                                                            0.0s
=> => extracting sha256:8663204ce13b2961da55026a2034abb9e5afaaccf6a9cfb44ad71406dcd07c7b                                                                                                                                                                                 0.2s
=> => sha256:2e8529c47e4629c394969b75f787ef6ac1c9d8cc16ba2b92aa97890a3119745d 453B / 453B                                                                                                                                                                                0.7s
=> => extracting sha256:8c392e9e905c179c05811b562acb9e9bb4161e4f967144b8908e744e205c342a                                                                                                                                                                                 1.5s
=> => extracting sha256:36ce72f2f1291c6db07fda7da4445166f00af667ef7d66774188186e26b88068                                                                                                                                                                                 0.1s
=> => extracting sha256:2e8529c47e4629c394969b75f787ef6ac1c9d8cc16ba2b92aa97890a3119745d                                                                                                                                                                                 0.0s
=> [stage-1 2/3] WORKDIR /home/node                                                                                                                                                                                                                                      0.2s
=> [stage-1 3/3] COPY --chown=node:node . .                                                                                                                                                                                                                              0.8s
=> exporting to image                                                                                                                                                                                                                                                    1.2s
=> => exporting layers                                                                                                                                                                                                                                                   1.2s
=> => writing image sha256:5e692de733be6dd7167ef10233fcd730d29ed8d6565d7b6ca9f584f44042b7f3                                                                                                                                                                              0.0s
=> => naming to docker.io/library/02-docker-multi-stage-build                                                                                                                                                                                                            0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
$ docker image ls
REPOSITORY                    TAG           IMAGE ID       CREATED          SIZE
02-docker-multi-stage-build   latest        5e692de733be   11 seconds ago   218MB
01-yarn-production            latest        e9de542100d3   3 minutes ago    1.77GB
00-initial                    latest        aea2fd476d32   9 minutes ago    1.94GB
```

```
$ docker history 02-docker-multi-stage-build
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
5e692de733be   24 seconds ago   CMD ["/bin/sh" "-c" "yarn start"]               0B        buildkit.dockerfile.v0
<missing>      24 seconds ago   COPY . . # buildkit                             106MB     buildkit.dockerfile.v0
<missing>      25 seconds ago   WORKDIR /home/node                              0B        buildkit.dockerfile.v0
<missing>      25 seconds ago   USER node                                       0B        buildkit.dockerfile.v0
<missing>      10 days ago      /bin/sh -c #(nop)  CMD ["node"]                 0B
<missing>      10 days ago      /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>      10 days ago      /bin/sh -c #(nop) COPY file:4d192565a7220e13…   388B
<missing>      10 days ago      /bin/sh -c apk add --no-cache --virtual .bui…   7.76MB
<missing>      10 days ago      /bin/sh -c #(nop)  ENV YARN_VERSION=1.22.18     0B
<missing>      10 days ago      /bin/sh -c addgroup -g 1000 node     && addu…   98.3MB
<missing>      10 days ago      /bin/sh -c #(nop)  ENV NODE_VERSION=16.15.0     0B
<missing>      4 weeks ago      /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B
<missing>      4 weeks ago      /bin/sh -c #(nop) ADD file:b9eae64dc6ab27fda…   5.59MB
```

### multi stage with cherry pick
```
$ docker build -t 02-docker-multi-stage-build-cp -f ./Dockerfile-with-cherry-picking .
[+] Building 28.5s (25/25) FINISHED
=> [internal] load build definition from Dockerfile-with-cherry-picking                                                                                                                                                                                                  0.0s
=> => transferring dockerfile: 1.19kB                                                                                                                                                                                                                                    0.0s
=> [internal] load .dockerignore                                                                                                                                                                                                                                         0.0s
=> => transferring context: 34B                                                                                                                                                                                                                                          0.0s
=> [internal] load metadata for docker.io/library/node:16-alpine3.14                                                                                                                                                                                                     1.4s
=> [internal] load metadata for docker.io/library/node:18.1.0-bullseye                                                                                                                                                                                                   1.4s
=> [auth] library/node:pull token for registry-1.docker.io                                                                                                                                                                                                               0.0s
=> [stage-1  1/10] FROM docker.io/library/node:16-alpine3.14@sha256:53a5c087654e75f8b12475fe143c5ab8b5f33254a37dc87743d066a57e67b4de                                                                                                                                     0.0s
=> [builder 1/8] FROM docker.io/library/node:18.1.0-bullseye@sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f                                                                                                                                     0.0s
=> [internal] load build context                                                                                                                                                                                                                                         0.7s
=> => transferring context: 968.36kB                                                                                                                                                                                                                                     0.7s
=> CACHED [stage-1  2/10] WORKDIR /home/node                                                                                                                                                                                                                             0.0s
=> CACHED [builder 2/8] RUN apt update                                                                                                                                                                                                                                   0.0s
=> CACHED [builder 3/8] RUN apt install build-essential                                                                                                                                                                                                                  0.0s
=> CACHED [builder 4/8] WORKDIR /home/node                                                                                                                                                                                                                               0.0s
=> [builder 5/8] COPY --chown=node:node . .                                                                                                                                                                                                                              0.8s
=> [builder 6/8] RUN yarn --frozen-lockfile --production                                                                                                                                                                                                                16.1s
=> [builder 7/8] RUN yarn build                                                                                                                                                                                                                                          7.7s
=> [builder 8/8] RUN rm -rf .cache                                                                                                                                                                                                                                       0.9s
=> [stage-1  3/10] COPY --from=builder --chown=node:node /home/node/package.json .                                                                                                                                                                                       0.0s
=> [stage-1  4/10] COPY --from=builder --chown=node:node /home/node/pages ./pages                                                                                                                                                                                        0.1s
=> [stage-1  5/10] COPY --from=builder --chown=node:node /home/node/public ./public                                                                                                                                                                                      0.1s
=> [stage-1  6/10] COPY --from=builder --chown=node:node /home/node/styles ./styles                                                                                                                                                                                      0.1s
=> [stage-1  7/10] COPY --from=builder --chown=node:node /home/node/.eslintrc.json .                                                                                                                                                                                     0.1s
=> [stage-1  8/10] COPY --from=builder --chown=node:node /home/node/next.config.js .                                                                                                                                                                                     0.1s
=> [stage-1  9/10] COPY --from=builder --chown=node:node /home/node/package.json .                                                                                                                                                                                       0.1s
=> [stage-1 10/10] COPY --from=builder --chown=node:node /home/node/yarn.lock .                                                                                                                                                                                          0.1s
=> exporting to image                                                                                                                                                                                                                                                    0.2s
=> => exporting layers                                                                                                                                                                                                                                                   0.2s
=> => writing image sha256:b54d81938fd1cae0203f523c2d0bb64d57de2efdc4ffae0bca1ee6a7cff9f2ad                                                                                                                                                                              0.0s
=> => naming to docker.io/library/02-docker-multi-stage-build-cp                                                                                                                                                                                                         0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
$ docker image ls
REPOSITORY                       TAG           IMAGE ID       CREATED          SIZE
02-docker-multi-stage-build-cp   latest        b54d81938fd1   5 seconds ago    112MB
02-docker-multi-stage-build      latest        5e692de733be   3 minutes ago    218MB
01-yarn-production               latest        e9de542100d3   6 minutes ago    1.77GB
00-initial                       latest        aea2fd476d32   12 minutes ago   1.94GB
```

```
$ docker history 02-docker-multi-stage-build-cp
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
b54d81938fd1   22 seconds ago   CMD ["/bin/sh" "-c" "yarn start"]               0B        buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/yarn.lock . # buildkit          76.1kB    buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/package.json . # buildkit       368B      buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/next.config.js . # buildkit     118B      buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/.eslintrc.json . # buildkit     40B       buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/styles ./styles # buildkit      1.97kB    buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/public ./public # buildkit      27kB      buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/pages ./pages # buildkit        2.54kB    buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/package.json . # buildkit       368B      buildkit.dockerfile.v0
<missing>      3 minutes ago    WORKDIR /home/node                              0B        buildkit.dockerfile.v0
<missing>      3 minutes ago    USER node                                       0B        buildkit.dockerfile.v0
<missing>      10 days ago      /bin/sh -c #(nop)  CMD ["node"]                 0B
<missing>      10 days ago      /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>      10 days ago      /bin/sh -c #(nop) COPY file:4d192565a7220e13…   388B
<missing>      10 days ago      /bin/sh -c apk add --no-cache --virtual .bui…   7.76MB
<missing>      10 days ago      /bin/sh -c #(nop)  ENV YARN_VERSION=1.22.18     0B
<missing>      10 days ago      /bin/sh -c addgroup -g 1000 node     && addu…   98.3MB
<missing>      10 days ago      /bin/sh -c #(nop)  ENV NODE_VERSION=16.15.0     0B
<missing>      4 weeks ago      /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B
<missing>      4 weeks ago      /bin/sh -c #(nop) ADD file:b9eae64dc6ab27fda…   5.59MB
```
