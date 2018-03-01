FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app

FROM base AS restore
COPY *.csproj ./
RUN donet restore

FROM restore AS build
RUN dotnet build -c Release -o /app

FROM build AS publish
COPY . ./
RUN dotnet publish -c Release -o /app

EXPOSE 80

FROM base AS final
WORKDIR /app
COPY --from=publish /app ./
ENTRYPOINT ["dotnet", "sample-app.dll"]
