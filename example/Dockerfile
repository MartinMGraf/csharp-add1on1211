# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM


# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

RUN apk add --no-cache \
    curl \
    icu-libs \
    libgcc \
    libstdc++ \
    unzip

RUN curl -sSLf -o MyAddon.zip "https://github.com/MartinMGraf/csharp-add1on12111x/releases/download/latest/MyAddon.zip" \
 && unzip MyAddon.zip -d /app \
 && rm MyAddon.zip
 && find /app


RUN chmod +x app/home/runner/work/csharp-add1on12111x/csharp-add1on12111x/example/src/bin/Release/net9.0/linux-musl-x64/publish/MyAddon
CMD ["/app/home/runner/work/csharp-add1on12111x/csharp-add1on12111x/example/src/bin/Release/net9.0/linux-musl-x64/publish/MyAddon"]
