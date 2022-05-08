FROM node:18.1.0-bullseye AS builder
## [Dockerfile](Dockerfile)

# install build tools because we can or some build step requires it :)
RUN apt update
RUN apt install build-essential

# switch to user provided by image
USER node
WORKDIR /home/node

# copy only needed parts of the code, also change owner of the file so docker user can access the files
COPY --chown=node:node . .

# install dependencies
RUN yarn --frozen-lockfile --production

# build project
RUN yarn build
RUN rm -rf .cache

FROM node:16-alpine3.14
USER node
WORKDIR /home/node

COPY --chown=node:node . .
#COPY --from=builder --chown=node:node /home/node/package.json .
#COPY --from=builder --chown=node:node /home/node/pages ./pages
#COPY --from=builder --chown=node:node /home/node/public ./public
#COPY --from=builder --chown=node:node /home/node/styles ./styles
#COPY --from=builder --chown=node:node /home/node/.eslintrc.json .
#COPY --from=builder --chown=node:node /home/node/next.config.js .
#COPY --from=builder --chown=node:node /home/node/package.json .
#COPY --from=builder --chown=node:node /home/node/yarn.lock .

# run server
CMD yarn start
