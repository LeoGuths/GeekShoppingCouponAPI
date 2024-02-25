FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /source
COPY . .
COPY ./.dockerignore /source
RUN dotnet restore "GeekShopping.CouponAPI.csproj" 
RUN dotnet publish "GeekShopping.CouponAPI.csproj" -c -release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
ENV ASPNETCORE_URLS=http://+:5020
COPY --from=build /app ./

EXPOSE 5020

ENTRYPOINT ["dotnet", "GeekShopping.CouponAPI.dll"]

#FROM mcr.microsoft.com/dotnet/runtime:8.0 AS base
#USER $APP_UID
#WORKDIR /app
#
#FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
#ARG BUILD_CONFIGURATION=Release
#WORKDIR /src
#COPY ["GeekShopping.CouponAPI/GeekShopping.CouponAPI.csproj", "GeekShopping.CouponAPI/"]
#RUN dotnet restore "GeekShopping.CouponAPI/GeekShopping.CouponAPI.csproj"
#COPY . .
#WORKDIR "/src/GeekShopping.CouponAPI"
#RUN dotnet build "GeekShopping.CouponAPI.csproj" -c $BUILD_CONFIGURATION -o /app/build
#
#FROM build AS publish
#ARG BUILD_CONFIGURATION=Release
#RUN dotnet publish "GeekShopping.CouponAPI.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "GeekShopping.CouponAPI.dll"]
