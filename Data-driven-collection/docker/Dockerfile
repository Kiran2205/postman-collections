# Use the official Node.js 20 image as the base image
FROM node:20

# Set the working directory in the container(linux)
WORKDIR /app

# Install Newman globally
RUN npm install -g newman

# Install Newman html report
RUN npm install -g newman-reporter-html

# Install Newman Reporter HTMLExtra
RUN npm install -g newman-reporter-htmlextra

# Ensure the 'results' directory exists
RUN mkdir -p /app/results

# Copy your Postman collection, test data files and environment files to the working directory
COPY data-driven-collection.json .
# Instead of using '.' to indicate copying to the current directory, we can use '/app' to be more explicit.
COPY data-driven-collection-environment.json /app 
COPY test-data/users-test-data.csv .

# Set the command to run Newman and execute your Postman collection
# By defauly without flag --reporter-htmlextra-report, the report will be generated in the default working directory which is '/app' with another folder 'newman' created inside it.
# If you want to change the location of the report, you can use the flag --reporter-htmlextra-export <path> to specify the path where you want to save the report.
CMD ["newman", "run", "data-driven-collection.json", "-e", "data-driven-collection-environment.json", "-d", "users-test-data.csv", "--verbose", "-r", "cli,json,html,htmlextra", "--reporter-htmlextra-export", "/app/results/data-driven-test-report.html"]