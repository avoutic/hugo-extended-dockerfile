## Image purpose

When you have a [Hugo](https://gohugo.io) project, it's not immediately obvious how you can publish your static site easily within a Docker-Compose or Kubernetes enviroment.

This image serves as the base for your Dockerfile you can put inside your Hugo project. When you build your Docker image from there, you have a simple way to serve your site from within a containerized environment.

## How to use this image

## Create a Dockerfile in your Hugo project

~~~
FROM avoutic/hugo-extended:latest

COPY . /src

RUN npm install --production
RUN hugo --destination=/target

FROM nginx
COPY --from=hugo /target /usr/share/nginx/html
~~~

You can just launch that docker image and you'll have your Hugo site published statically.
