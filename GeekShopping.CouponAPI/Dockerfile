FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /source
COPY . .
RUN dotnet restore "GeekShopping.CouponAPI.csproj" 
RUN dotnet publish "GeekShopping.CouponAPI.csproj" -c -release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
ENV ASPNETCORE_URLS=http://+:5020
COPY --from=build /app ./

EXPOSE 5020

ENTRYPOINT ["dotnet", "GeekShopping.CouponAPI.dll"]