https://medium.com/@jaydeepvpatil225/hosting-net-core-web-api-images-with-docker-compose-over-https-2ee70dc877ec

Create certificate directory on my PC
dotnet dev-certs https -ep $env:userprofile\.aspnet\https\aspnetapp.pfx -p password
This has a password of "password"

dotnet dev-certs https --trust
Trusting the HTTPS development certificate was requested. A confirmation prompt will be displayed if the certificate was not previously trusted. Click yes on the prompt to trust the certificate.

docker run -p 8081:80 -p 8082:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=7001 -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/aspnetapp.pfx -v $env:USERPROFILE\.aspnet\https:/https/ ssldemo

http://localhost:8081/swagger/index.html 
if it works then image will appear (tlsworking.png)