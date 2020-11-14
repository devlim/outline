# 1 Clone https://github.com/outline/outline repo

```
git clone https://github.com/outline/outline
```

# 2 Install dependency

```
sudo docker run -u $(id -u):$(id -g) --rm -v $(pwd):/home -w="/home" node:14-alpine yarn install
```

# 3 Clone .env.sample to .env

```
cp .env.sample .env
```

# 3.1 Update following .env value

1. SECRET_KEY - On terminal, run `openssl rand -hex 32` to generate .env
2. DATABASE_URL - Update to postgres://user:pass@postgres:5432/outline
3. DATABASE_URL_TEST - Update to postgres://user:pass@postgres:5432/outline-test`
4. REDIS_URL - Update to redis://redis:6379`
5. Register a Slack app at https://api.slack.com/apps to get Slack app credentials to update SLACK_KEY,SLACK_SECRET,SLACK_VERIFICATION_TOKEN, SLACK_APP_ID
6. Update SMTP_HOST, SMTP_PORT, SMTP_USERNAME, SMTP_PASSWORD, SMTP_FROM_EMAIL, SMTP_REPLY_EMAIL for email(notification, invitation, etc) to work

# 4 Docker compose up to run Outline

```
docker-compose up -d
```

# 5 Run migration file

```
docker-compose exec outline yarn sequelize db:migrate
```

# 6 Test drive by opening a browser and navigate to localhost:3000