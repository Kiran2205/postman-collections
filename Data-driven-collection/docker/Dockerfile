# Use the official Node.js 20 image as the base image
FROM node:20

# Set the working directory in the container(linux)
WORKDIR /app

# Install Newman globally
RUN npm install -g newman

#Install Newman html report
RUN npm install -g newman-reporter-html

#Install Newman Reporter HTMLExtra
RUN npm install -g newman-reporter-htmlextra

# Copy your Postman collection, test data files and environment files to the working directory
COPY data-driven-collection.json .
COPY data-driven-collection-environment.json .
COPY test-data/users-test-data.csv .

# Set the command to run Newman and execute your Postman collection
CMD ["newman", "run", "data-driven-collection.json", "-e", "data-driven-collection-environment.json", "-d", "users-test-data.csv", "--verbose", "-r", "cli,json,html,htmlextra"]