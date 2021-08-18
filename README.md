# express-react-nextjs
Fullstack web application template entirely in Typescript. Uses: Express, React,
GraphQL, Postgres, and JWT authentication. Inspired by [this YouTube video](https://www.youtube.com/watch?v=I6ypD7qv3Z8).
# docker deployment
Once again Docker!!! Using docker-compose to run multicontainers.
- Read each README in `client` and `server` to set environment variables.
- Run `docker-compose up --build`
- Find service at `http://localhost:3000`
# AWS Deployment
Deploys application on AWS stack: VPC + Load balancer + ECS on EC2 + RDS on Postgres.
Charges will incur for AWS resources.
- Follow instructions in CDK package to deploy stack
# Heroku + Vercel deployment
Backend service on heroku with frontend service on Vercel.
## Push server to Heroku
Using Heroku CLI or Heroku website.

The following is steps for invoking the `setup` portion of heroku.yml
- `heroku update beta`
- `heroku plugins:install @heroku-cli/plugin-manifest` (if not already installed)
- `heroku create <your-app-name> --manifest`

Othwerise, please follow
- Set up heroku dyno on website or thru cli
- Install postgres addon on website or thru cli
- `heroku stack:set container` (let heroku know this is a Docker contianer stack)

Now follow:
- `heroku git:remote -a <appname>` (to set heroku remote in your local repo)
- `heroku config:set PGSSLMODE=no-verify` (otherwise error will occur)
- `heroku config:set ACCESS_TOKEN_SECRET=<secret here>`
- `heroku config:set REFRESH_TOKEN_SECRET=<secret here>`
- `heroku config:set CORS_ORIGIN=<value>` (Vercel link, domain name, etc.)
- `git push heroku master`