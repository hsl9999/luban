FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /app/Luban.Common
COPY Luban.Common/*.csproj ./
COPY Luban.Common/Source ./Source
COPY Luban.Common/.editorconfig .
COPY nuget.config ./nuget.config

WORKDIR /app/Luban.Client
COPY Luban.Client/Luban.Client.csproj ./
COPY Luban.Client/.editorconfig .
COPY Luban.Client/Source ./Source
COPY nuget.config ./nuget.config

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/runtime:5.0 AS runtime
WORKDIR /app
COPY --from=build /app/Luban.Client/out ./

ENTRYPOINT ["/app/Luban.Client"]