Process of deploying React App to AWS Amplify

1. Create React App `npx create-react-app [project-name]`

2. Create `Github` repo and connect to it

3. Login to your AWS account and go to Amplify

4. Choose Host your web app and choose `Github` as source

5. Accept the default build settings and deploy

6. AWS will now build your source code and deploy to your app hosted at a random adress with .amplifyapp.com at the end...

7. Pushing the changes from your main/master branch will automatically trigger a new build in the AWS Amplify Service and your changes will be live
