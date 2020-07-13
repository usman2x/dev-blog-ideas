### Deploy create react app using nginx on shared hosting
1. Create React app
2. Build react app with relative path
3. Dockerize react app
4. Deploy

#### How to create relative path
- Add `"homepage":"./"` in `package.json`
- `npm run build` will create build using relative path
- Create directory on shared hosting `/nginx/html/MyDirectory`
- Copy content from build directory and paste into `/nginx/html/MyDirectory`

#### How to deploy react app in docker container nginx
`FROM node:XXX as builImage`

`...............`

`FROM nginx:1.15.12-alpine`

`RUN mkdir -p /usr/share/nginx/html/MyDirectory`

`COPY --from=buildImage /usr/src/app/build /usr/share/nginx/html/MyDirectory`

`EXPOSE 80`
