Weather API
-----------

dotnet dev-certs https --trust

dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\WeatherAPI.pfx -p pa55w0rd!

dotnet user-secrets set "Kestrel:Certificates:Development:Password" "pa55w0rd!"

dotnet user-secrets set "CertPassword" "pa55w0rd!"

docker run --name first-weather-webapi-https-container -d -p 8080:80 -p 8081:443 damilolaadegunwa/weather-webapi-https

docker run --name first-weather-webapi-https-container -d -p 1070:80 -p 1071:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=1071 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:/root/.microsoft/usersecrets -v $env:USERPROFILE\.aspnet\https:/root/.aspnet/https/ damilolaadegunwa/weather-webapi-https