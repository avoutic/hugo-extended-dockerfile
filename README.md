# How to use this image

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
