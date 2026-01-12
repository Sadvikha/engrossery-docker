# ✅ Use Node version compatible with Vite 7
FROM node:22

# Set working directory
WORKDIR /app

# Copy dependency files first (cache-friendly)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy rest of the source code
COPY . .

# Vite dev server port
EXPOSE 5173

# Start Vite and expose externally
CMD ["npm", "run", "dev", "--", "--host"]
