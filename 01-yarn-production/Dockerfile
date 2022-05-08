FROM node:18.1.0-bullseye

# install build tools because we can or some build step requires it :)
RUN apt update
RUN apt install build-essential

# switch to user provided by image
USER node
WORKDIR /home/node

COPY --chown=node:node . .

# install dependencies
RUN yarn --frozen-lockfile --production

# build project
RUN yarn build

# run server
CMD yarn start

