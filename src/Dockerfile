FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

ARG DEBIAN_FRONTEND noninteractive

RUN mkdir /src
WORKDIR /src
ADD RandomQuotes /src
RUN dotnet restore
RUN ["dotnet", "build", "--configuration", "release"]

EXPOSE 5000 5001

ENV ASPNETCORE_URLS="http://+:5000;https://+:5001"
ENV ASPNETCORE_ENVIRONMENT="Production"
RUN ["dotnet", "dev-certs", "https"]

ENTRYPOINT [ "dotnet", "run", "--no-launch-profile" ]