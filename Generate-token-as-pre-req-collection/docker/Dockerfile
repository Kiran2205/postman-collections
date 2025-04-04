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

# Copy your Postman collection and environment files to the working directory
COPY generate-token-as-pre-requisite-collection.json .
COPY generate-token-as-pre-requisite-env.json .

# Set the command to run Newman and execute your Postman collection
#By defauly without flag --reporter-htmlextra-report, the report will be generated in the default working directory which is '/app' with another folder 'newman' created inside it.
# If you want to change the location of the report, you can use the flag --reporter-htmlextra-export <path> to specify the path where you want to save the report.
CMD ["newman", "run", "generate-token-as-pre-requisite-collection.json", "-e", "generate-token-as-pre-requisite-env.json", "--verbose", "-r", "cli,json,html,htmlextra"]