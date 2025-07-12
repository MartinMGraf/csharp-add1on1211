ARG BUILD_FROM

# BUILD FROM dotnet SDK to compile die App
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY ./src/ ./
RUN dotnet publish -c Release -r linux-arm64 --self-contained true -p:AssemblyName=MyAddon -o /out

# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
FROM $BUILD_FROM


# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

COPY --from=build /out /app
WORKDIR /app

RUN chmod +x /app/MyAddon
CMD ["/app/MyAddon"]
