# Use a minimal base image
FROM alpine:latest

# Install required packages
RUN apk add --no-cache git

# Create a .gitconfig file
COPY configs/.gitconfig /root/.gitconfig
