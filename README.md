# README

# Development ennvironment
    Ruby version - 3.0.4
    `bundle` to manage Ruby gems

# Rails credentials
    We use encrypted credentials per environment with separate RAILS_MASTER_KEYs (which are stored in a shared LastPass folder named "Shared-CT Notifications").
    To edit credentials, use `RAILS_MASTER_KEY=<<Value from LastPass specifice to environment>> bin/rails credentials:edit --environment <<environment_name>>`.

# General Setup
1. Install Homebrew: https://brew.sh/
1. Install RBENV: https://github.com/rbenv/rbenv
1. Setup the right version of ruby
    ```
   rbenv install 3.0.4
   rbenv local 3.0.4
1. Install postgres with rbenv:  
    ```
   brew install postgresql
1. Start postgres: 
    ```
   brew services start postgresql
1. Clone the repo
    ```
   git clone https://github.com/xdotcommer/co-notifications
2. Setup rails app and database 
    ```
   cd co-notifications
   bundle install
   rake db:create
   rake db:migrate
   rake db:seed
   

# Running tests
    bin/rspec

# Configuration/Environments

| App | Database | Twilio | S3 Instance / Bucket | Stack | Environment |
|-----|----------|--------|----|-------| ------------|
| notifications-staging | notifications-staging-db | CfA SNIL | CfA SNIL / notifications-staging-csvs | shared-us-west-1 | innovation-lab-staging |
| notifications-production | notifications-production-db | CT | CfA SNIL / notifications-production-csvs | snil-ct-production | snil-ct-msg-pilot-prod |

# Environment variables

1. AWS_ACCESS_KEY_ID
1. AWS_REGION
1. AWS_SECRET_ACCESS_KEY
1. DATABASE_URL
1. RAILS_ENV
1. RAILS_LOG_TO_STDOUT
1. RAILS_MASTER_KEY
1. TWILIO_ACCOUNT_SID
1. TWILIO_MESSAGING_SERVICE_SID
1. TWILIO_AUTH_TOKEN


# Deployment
- We use [Dockerfile Deploy](https://deploy-docs.aptible.com/docs/dockerfile-deploy)
- Configure your git remotes for staging and production, e.g., `git remote add aptible-production git@beta.aptible.com:snil-ct-msg-pilot-prod/notifications-production.git`.
- Deploy using git push: `git push aptible-production main:master`
