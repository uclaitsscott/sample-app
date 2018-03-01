FROM microsoft/aspnetcore:2.0 AS base
ARGH source
WORKDIR /app
EXPOSE 80
RUN dotnet restore
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", "sample-app.dll"]
