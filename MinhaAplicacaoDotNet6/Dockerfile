# Use the .NET 6 SDK image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the project file and restore dependencies
COPY ./MinhaAplicacaoDotNet6/MinhaAplicacaoWeb/*.csproj ./
RUN dotnet restore

# Copy the remaining files
COPY ./MinhaAplicacaoDotNet6/MinhaAplicacaoWeb/ ./

# Build the application
RUN dotnet publish -c Release -o out

# Build the runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /app
COPY --from=build /app/out ./
ENTRYPOINT ["dotnet", "MinhaAplicacaoWeb.dll"]
