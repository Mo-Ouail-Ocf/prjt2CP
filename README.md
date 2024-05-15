# PRJP 2CP N06

## Deployment Notice
### Required packages
-	docker
-	docker compose plugin
-	openssl

### Cloning the project

```sh
git clone --recurse-submodules https://github.com/Mo-Ouail-Ocf/prjt2cp
```

### Setting up the environment
First copy the `.env.sample` to `.env` 
```sh
cp .env.sample .env
```
then fill the variables with the values discussed bellow
### Getting Google OAuth2 Credentials
follow this [guide](https://analytify.io/get-google-client-id-and-client-secret/) to generate the Google OAuth Credentials 

>NOTE: the user type is internal
> NOTE: Make sure that the URL of the Backend and Frontend are in the `Authorised redirect URIs` and `Authorised JavaScript origins` lists
#### Generating Secret Keys
Generating the `ACCESS_TOKEN_SECRET_KEY` and `REFRESH_TOKEN_SECRET_KEY` is as easy as running the following command:
```sh
openssl rand -hex 32
```
### Database 
The Database URL should look like this: 
```
DATABASE_URL=postgresql://postgres:password@database/Prjt2cp-database
```
More, on general:
```
DATABASE_URL="postgresql://postgres:{POSTGRES_PASSWORD}@database/{POSTGRES_DB}"
```
Knowing that `POSTGRES_PASSWORD` and `POSTGRES_DB` are set in the `docker-compose.yml`
### Domain Name
The client requires the `VITE_API_DOMAIN` to be set.
> For testing on one computer: `VITE_API_DOMAIN="localhost:8000"`
> For LAN: `VITE_API_DOMAIN="{ip_address}:8000"`
###  Email Configuration
Create an new Google Account and fill the environment variables in `.env` under the `Email` tag.
> NOTE: `MAIL_USERNAME` is the email address

### Chat Bot
The chat bot requires the `OPENAI_TOKEN` variable to be set. It is possible to obtain a token by following this [guide](https://www.guidingtech.com/how-to-generate-openai-api-key/) .

### Deploying
Having the steps above satisfied, the deployment can be done with just one single command
```sh
docker compose up --build
```
> NOTE: it will take a lot of time on first time
