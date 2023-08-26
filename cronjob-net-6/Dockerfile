FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["CronWorkerService/CronWorkerService.csproj", "CronWorkerService/"]
RUN dotnet restore "CronWorkerService/CronWorkerService.csproj"
COPY . .
WORKDIR "/src/CronWorkerService"
RUN dotnet build "CronWorkerService.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "CronWorkerService.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "CronWorkerService.dll"]