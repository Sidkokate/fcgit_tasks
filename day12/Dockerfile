# Use an official Node.js runtime as a base image
FROM node AS build
# Set the working directory in the container
WORKDIR /usr/src/app
# Copy package.json and package-lock.json to the working directory
COPY package.json .
COPY index.js .
COPY . .
# Install application dependencies
RUN npm install
CMD ["node","index.js"]
# Copy the application code to the working directory


FROM node AS production
WORKDIR /usr/src/app
#copy req file for ecicution
COPY --from=build /usr/src/app ./dist
COPY --from=build /usr/src/app/package*.json ./
RUN npm install
# Expose the port your app will run on
EXPOSE 3000
# Command to run your application
CMD ["node","dist/index.js"]
