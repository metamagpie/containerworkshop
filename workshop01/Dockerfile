FROM node:latest

# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

# Create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
# Files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views

# Run some command
RUN npm install

# How an image is provisioned/run

# What port our container will be exposing
EXPOSE ${APP_PORT}

# Add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

ENTRYPOINT [ "node", "main.js" ]

CMD [ "" ]
