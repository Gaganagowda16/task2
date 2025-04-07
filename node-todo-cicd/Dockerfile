# Use Node.js base image
FROM node:12.2.0-alpine

# Set the working directory inside the container
WORKDIR /node

# Copy everything from your project to the container
COPY . .

# Install dependencies and run tests (combine into one RUN)
RUN npm install && npm run test

# Expose port 8000
EXPOSE 8000

# Start the app
CMD ["node", "app.js"]

