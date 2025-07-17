# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM


# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

RUN apk add --no-cache \
    unzip nginx \
  && mkdir -p /run/nginx
  
#Copy our conf into the nginx http.d folder.
COPY ingress.conf /etc/nginx/http.d/


RUN curl -sSLf -o MyAddon.zip "https://github.com/MartinMGraf/csharp-add1on12111x/releases/download/latest/MyAddon5.zip" \
 && unzip MyAddon.zip -d /app \
 && rm MyAddon.zip 
 
RUN chmod +x /app/home/runner/work/csharp-add1on12111x/csharp-add1on12111x/aot-publish/out/MyAddon
CMD [ "nginx","-g","daemon off;error_log /dev/stdout debug;" ]
CMD ["/app/home/runner/work/csharp-add1on12111x/csharp-add1on12111x/aot-publish/out/MyAddon"]
