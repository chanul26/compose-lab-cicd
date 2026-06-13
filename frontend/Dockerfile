# ========================================
# STAGE 1: The Heavy Builder
# ========================================
FROM node:20 AS builder

WORKDIR /app
# We copy EVERYTHING into the heavy builder (including the 150MB mock file)
COPY . .

# ========================================
# STAGE 2: The Tiny Production Runner
# ========================================
# We start a brand new, tiny Nginx container
FROM nginx:alpine

# We reach into the 'builder' stage and steal ONLY the clean HTML file
COPY --from=builder /app/index.html /usr/share/nginx/html/index.html

# The builder stage and the 150MB node_modules file are now deleted automatically!
