FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run build

# Create the nginx server and connect the two
FROM nginx
EXPOSE 3000
# Copy from the first part (0) 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html