# Use Ionic base image
FROM beevelop/ionic as ionic

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

RUN ionic build

FROM nginx:alpine
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
