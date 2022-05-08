## Squash

docker config
```
{
  ...
  "experimental": true,
  ...
}
```

```
$ docker build -t 03-nextjs-standalone-sq . --squash
[+] Building 27.6s (17/17) FINISHED
=> [internal] load build definition from Dockerfile                                                                                                                                                                                                                      0.0s
=> => transferring dockerfile: 688B                                                                                                                                                                                                                                      0.0s
=> [internal] load .dockerignore                                                                                                                                                                                                                                         0.0s
=> => transferring context: 34B                                                                                                                                                                                                                                          0.0s
=> [internal] load metadata for docker.io/library/node:16-alpine3.14                                                                                                                                                                                                     0.7s
=> [internal] load metadata for docker.io/library/node:18.1.0-bullseye                                                                                                                                                                                                   0.7s
=> [builder 1/8] FROM docker.io/library/node:18.1.0-bullseye@sha256:71c779ea8a157e6efadcafdae79f00fb39b7f3fdb2819ebef3984315c281540f                                                                                                                                     0.0s
=> [stage-1 1/3] FROM docker.io/library/node:16-alpine3.14@sha256:53a5c087654e75f8b12475fe143c5ab8b5f33254a37dc87743d066a57e67b4de                                                                                                                                       0.0s
=> [internal] load build context                                                                                                                                                                                                                                         0.9s
=> => transferring context: 14.65MB                                                                                                                                                                                                                                      0.9s
=> CACHED [builder 2/8] RUN apt update                                                                                                                                                                                                                                   0.0s
=> CACHED [builder 3/8] RUN apt install build-essential                                                                                                                                                                                                                  0.0s
=> CACHED [builder 4/8] WORKDIR /home/node                                                                                                                                                                                                                               0.0s
=> [builder 5/8] COPY --chown=node:node . .                                                                                                                                                                                                                              1.1s
=> [builder 6/8] RUN yarn --frozen-lockfile --production                                                                                                                                                                                                                16.2s
=> [builder 7/8] RUN yarn build                                                                                                                                                                                                                                          6.1s
=> [builder 8/8] RUN rm -rf .cache                                                                                                                                                                                                                                       1.0s
=> CACHED [stage-1 2/3] WORKDIR /home/node                                                                                                                                                                                                                               0.0s
=> [stage-1 3/3] COPY --from=builder --chown=node:node /home/node/.next/standalone ./                                                                                                                                                                                    0.1s
=> exporting to image                                                                                                                                                                                                                                                    0.1s
=> => exporting layers                                                                                                                                                                                                                                                   0.1s
=> => writing image sha256:6f909a13d2ba197da2ed02dd61cd47c34eb37290bcfbd2894e64e4bcf861ca86                                                                                                                                                                              0.0s
=> => naming to docker.io/library/03-nextjs-standalone-sq                                                                                                                                                                                                                0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```
$ docker image ls
REPOSITORY                          TAG           IMAGE ID       CREATED              SIZE
03-nextjs-standalone-sq             latest        f4b350889317   7 seconds ago        117MB
02-docker-multi-stage-build-cp-sq   latest        3f3759a39066   57 seconds ago       111MB
02-docker-multi-stage-build-sq      latest        4d19e9799710   About a minute ago   217MB
01-yarn-production-sq               latest        ac2d8c6e85ed   2 minutes ago        1.76GB
00-initial-sq                       latest        f881b9bffc9f   2 minutes ago        1.76GB
03-nextjs-standalone                latest        622fdc1f1157   5 minutes ago        118MB
02-docker-multi-stage-build-cp      latest        b54d81938fd1   8 minutes ago        112MB
02-docker-multi-stage-build         latest        5e692de733be   11 minutes ago       218MB
01-yarn-production                  latest        e9de542100d3   14 minutes ago       1.77GB
00-initial                          latest        aea2fd476d32   20 minutes ago       1.94GB
```

```
$ docker history 03-nextjs-standalone-sq
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
f4b350889317   21 seconds ago                                                   117MB     create new from sha256:6f909a13d2ba197da2ed02dd61cd47c34eb37290bcfbd2894e64e4bcf861ca86
<missing>      22 seconds ago   CMD ["/bin/sh" "-c" "node server"]              0B        buildkit.dockerfile.v0
<missing>      22 seconds ago   COPY /home/node/.next/standalone ./ # buildk…   0B        buildkit.dockerfile.v0
<missing>      11 minutes ago   WORKDIR /home/node                              0B        buildkit.dockerfile.v0
<missing>      11 minutes ago   USER node                                       0B        buildkit.dockerfile.v0
<missing>      10 days ago      /bin/sh -c #(nop)  CMD ["node"]                 0B
<missing>      10 days ago      /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>      10 days ago      /bin/sh -c #(nop) COPY file:4d192565a7220e13…   0B
<missing>      10 days ago      /bin/sh -c apk add --no-cache --virtual .bui…   0B
<missing>      10 days ago      /bin/sh -c #(nop)  ENV YARN_VERSION=1.22.18     0B
<missing>      10 days ago      /bin/sh -c addgroup -g 1000 node     && addu…   0B
<missing>      10 days ago      /bin/sh -c #(nop)  ENV NODE_VERSION=16.15.0     0B
<missing>      4 weeks ago      /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B
<missing>      4 weeks ago      /bin/sh -c #(nop) ADD file:b9eae64dc6ab27fda…   0B
```
