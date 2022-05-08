FROM node:18.1.0-bullseye AS builder

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

COPY --from=builder --chown=node:node /home/node/.next/standalone ./

# run server
CMD node server
