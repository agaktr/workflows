# Configure the .env file

This is for development server only. (ex. blackflag.cloud)
```bash
#copy the .env file and rename it to .env.local
cp .env .env.local
```

```dotenv
#edit the .env.local file and set the database credentials
DATABASE_URL="//${DB_USER}:${DB_PASSWORD}@${DB_HOST}:${DB_PORT}/${DB_NAME}?serverVersion=${DB_VERSION}"

#set the MAILER_DSN with sendgrid api key
#you can get a free sendgrid account here: https://signup.sendgrid.com/
MAILER_DSN=sendgrid://${SENDGRID_API_KEY}@default

#set the hwioauth credentials
#you can create an app on the following links:
#facebook: https://developers.facebook.com/apps/
#google: https://console.cloud.google.com/apis/credentials
#apple: https://developer.apple.com/account/resources/identifiers/list
{social}_ID=
{social}_SECRET=
```

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step13.md" align="right">Next: Create database</a>
</div>  
