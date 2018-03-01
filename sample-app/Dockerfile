FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# build runtime image
FROM microsoft/aspnetcore:2.0 
WORKDIR /app
COPY --from=base /app/out ./
ENTRYPOINT ["dotnet", "sample-app.dll"]
