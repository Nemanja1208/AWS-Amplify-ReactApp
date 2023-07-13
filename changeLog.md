Process of deploying React App to AWS Amplify

1. Create React App `npx create-react-app [project-name]`

2. Create `Github` repo and connect to it

3. Login to your AWS account and go to Amplify

4. Choose Host your web app and choose `Github` as source

5. Accept the default build settings and deploy

6. AWS will now build your source code and deploy to your app hosted at a random adress with .amplifyapp.com at the end...

7. Pushing the changes from your main/master branch will automatically trigger a new build in the AWS Amplify Service and your changes will be live

# Extra

8. Now that we have initialized a new Amplify project in our account, we want to bring it down into our local environment so we can continue development and add new features.

9. We install Amplify CLI `npm install -g @aws-amplify/cli`

10. We configure the Amplify CLI by running `amplify configure` - `https://docs.amplify.aws/cli/start/install/#configure-the-amplify-cli`

10a. We first choose a region in which our account or app is setup

10b. We create a new user that is gonna access our Amplify Service through this CLI

10c. We attach policy directly AdministratorAccess-Amplify

10d. After we have created a User with Policy attached we need to create a access key for CLI

10e. We add the ID and Secret Key it to the CLI prompt and we have successfully configured our Amplify CLI (local machine)

# Adding Authentication
