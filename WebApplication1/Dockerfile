FROM microsoft/aspnetcore-build:2.0.0 AS build
WORKDIR /code
COPY . .
RUN dotnet restore -p:RestoreUseSkipNonexistentTargets=false -nowarn:msb3202,nu1503

RUN dotnet publish --output /output --configuration Release

FROM microsoft/aspnetcore:latest
COPY --from=build /output /app
WORKDIR /app
ENTRYPOINT ["dotnet","WebApplication1.dll"]