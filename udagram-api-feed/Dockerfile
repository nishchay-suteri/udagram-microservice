# Use NodeJS base image
FROM node:13

# For Environment variable usage
ARG POSTGRES_USERNAME
ENV POSTGRES_USERNAME=$POSTGRES_USERNAME
ARG POSTGRES_PASSWORD
ENV POSTGRES_PASSWORD=$POSTGRES_PASSWORD
ARG POSTGRES_HOST
ENV POSTGRES_HOST=$POSTGRES_HOST
ARG POSTGRES_DB
ENV POSTGRES_DB=$POSTGRES_DB
ARG AWS_BUCKET
ENV AWS_BUCKET=$AWS_BUCKET
ARG AWS_REGION
ENV AWS_REGION=$AWS_REGION
ARG AWS_PROFILE
ENV AWS_PROFILE=$AWS_PROFILE
ARG JWT_SECRET
ENV JWT_SECRET=$JWT_SECRET
ARG URL
ENV URL=$URL

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy app source
COPY . .

# Bind the port that the image will run on
EXPOSE 8080

# Define the Docker image's behavior at runtime
CMD ["npm", "run", "dev"]
