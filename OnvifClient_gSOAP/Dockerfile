# Use an Alpine Linux image with CMake and build tools
FROM alpine:latest

# Install required packages: build tools, CMake, and any dependencies
RUN apk add --no-cache \
    build-base \
    cmake \
    libc6-compat

# Set the working directory
WORKDIR /app

# Copy the project files into the container
COPY . /app

# Create a build directory
RUN mkdir build

# Change to the build directory
WORKDIR /app/build

# Configure the build and generate the makefiles
RUN cmake ..

# Build the shared library
RUN make

# Optionally, install the shared library (e.g., to /usr/local/lib)
RUN make install

# Clean up build tools if you don't need them in the final image
RUN apk del build-base cmake

# Set the environment variables if needed
ENV LD_LIBRARY_PATH /usr/local/lib

WORKDIR ~/

# Optionally, clean up source code or other files that are not needed in the final image
RUN rm -rf /app/*
