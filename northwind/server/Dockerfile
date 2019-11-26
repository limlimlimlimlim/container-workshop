FROM node:latest

# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=172.17.0.4
ENV DB_PORT=3306
ENV DB_USER=root
ENV DB_PASSWORD=changeit

# create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views
ADD config config

# run some command - during build time
RUN npm install

## How an image is provision/run

# what port our container will be exposing
EXPOSE ${APP_PORT}

# add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -f http://172.17.0.4:${APP_PORT}/health > /dev/null || exit 1

# node main.js 3000
ENTRYPOINT ["node", "main.js"]

CMD [""]