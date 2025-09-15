# Base image: Node.js 18 LTS
FROM node:18-slim

# Create and set the app directory
WORKDIR /usr/src/app

# Copy dependency manifests first
COPY ./package*.json ./

# Install patched PostCSS + safe parser first, then dependencies
RUN npm install --no-audit --no-fund postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps \
    && npm install --legacy-peer-deps

# Copy application source
COPY . .

# Set environment variables
ENV PORT=3000 \
    NODE_OPTIONS=--openssl-legacy-provider

# Expose the app port
EXPOSE ${PORT}

# Provide default command
ENTRYPOINT ["npm", "start"]
