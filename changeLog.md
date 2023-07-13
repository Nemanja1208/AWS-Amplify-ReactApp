Process of deploying React App to AWS Amplify

1. Create React App `npx create-react-app [project-name]`

2. Create `Github` repo and connect to it

3. Login to your AWS account and go to Amplify

4. Choose Host your web app and choose `Github` as source

5. Accept the default build settings and deploy

6. AWS will now build your source code and deploy to your app hosted at a random adress with .amplifyapp.com at the end...

7. Pushing the changes from your main/master branch will automatically trigger a new build in the AWS Amplify Service and your changes will be live

# Amplify CLI Configuration for local development

8. Now that we have initialized a new Amplify project in our account, we want to bring it down into our local environment so we can continue development and add new features.

9. We install Amplify CLI `npm install -g @aws-amplify/cli`

10. We configure the Amplify CLI by running `amplify configure` - `https://docs.amplify.aws/cli/start/install/#configure-the-amplify-cli`

10a. We first choose a region in which our account or app is setup

10b. We create a new user that is gonna access our Amplify Service through this CLI

10c. We attach policy directly AdministratorAccess-Amplify

10d. After we have created a User with Policy attached we need to create a access key for CLI

10e. We add the ID and Secret Key it to the CLI prompt and we have successfully configured our Amplify CLI (local machine)

# Adding Authentication

11. Installing libraries `npm install aws-amplify @aws-amplify/ui-react`

12. For some reason we need to run `amplify init` in order to start adding authorization and other services

13. Adding Authorization through Amplify `amplify add auth` and we choose default auth and security config and `Username` as sign in

14. We deploy the Auth to Amplify with `amplify push --y` - This will trigger AWS CloudFormation, AWS Congito, Lambda and IAM Policy to create some necessary configuration

15. We configure React in index.js and App.js

# Setting up CI/CD for frontend/backend

16. Run `amplify console` to open the Amplify console. From the navigation pane, choose `App settings > Build settings`.

17. Modify it to add the backend section (lines 2-7 in the code below) to your `amplify.yml`. After making the edits, choose Save.

```version: 1
backend:
  phases:
    build:
      commands:
        - '# Execute Amplify CLI with the helper script'
        - amplifyPush --simple
frontend:
  phases:
    preBuild:
      commands:
        - yarn install
    build:
      commands:
        - yarn run build
  artifacts:
    baseDirectory: build
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```

18. Editing Build image settings and choosing Amplify CLI as package version override

19. Go to Frontend branch in Amplify App Home and edit so that the backend environment is `staging`

19a. If you get a `setup a service role` ERROR, follow the instructions from there and you should be good.
