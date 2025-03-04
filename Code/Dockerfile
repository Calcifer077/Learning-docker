# What is the bare minimum requirement of your app. It needs 'node'.
FROM node:19-alpine

# We also need all the files for our application. So we are moving them to a different location inside a docker cotnainer. Where 'app' is the name of that directory.
COPY package.json /app/
COPY src /app/

# Move to that directory.
WORKDIR /app

# Install all the necessary file for your application
RUN npm install

# Run your app. There can only be one 'CMD' command in your dockerfile
CMD ["node", "server.js"]

# To Build a image
# docker build -t node-app:1.0.0 . 
#  build a docker image with 'node-app' name and a version of '1.0.0'. '.' represents the current directory where this docker file is located.
# If you were to run 'docker images' you will find 'node-app' in it. Now you can run this image like you usually do using above commands
