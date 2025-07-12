# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM


# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

RUN apk add --no-cache unzip curl

RUN curl -sSLf -o MyAddon.zip "https://github.com/MartinMGraf/csharp-addon1211/releases/download/latest/MyAddon.zip" \
 && unzip MyAddon.zip -d /app \
 && rm MyAddon.zip

RUN ls -la /

RUN chmod +x app/MyAddon
RUN app/MyAddon
