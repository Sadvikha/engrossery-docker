# Use modern Node (safe & consistent)
FROM node:22

# Set working directory
WORKDIR /app

# Copy dependency files first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy backend source code
COPY . .

# Expose backend port (CHANGE if your app uses another port)
EXPOSE 5000

# Start backend server
CMD ["npm", "start"]
