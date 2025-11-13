# Use NodeJS Version from Build Args (For docker-compose Compatibility)
ARG NODE_VERSION=24
FROM node:${NODE_VERSION}-alpine

# Set Working Directory
WORKDIR /app

# Install Dependencies for Better Build Performance
RUN apk add --no-cache libc6-compat

# Copy Package Files
COPY package*.json ./

# Install Dependencies (Only Production Dependencies)
RUN npm ci --only=production

# Copy All Project Files
COPY . .

# Build the NextJS Application
RUN npm run build

# Expose Port 3000
EXPOSE 3000

# Set Environment to Production
ENV NODE_ENV=production
ENV PORT=3000

# Start the NextJS Application
CMD ["npm", "start"]