# AWS Amplify 
AWS Amplify provides a Git-based CI/CD workflow for building, deploying, and hosting single-page web applications or static sites with serverless backends. Upon connecting to a Git repository, Amplify determines the build settings for both the frontend framework and any serverless backend resources configured with the Amplify CLI, and automatically deploys updates with every code commit.

## Deploy and Host React App
- Create new React App
- Initialize GitHub
- Log in to AWS Management Console
- Deploy app with AWS Amplify
![Alt text](/public/get-started.png?raw=true "Get Started")
![Alt text](/public/select-github.png?raw=true "Deploy")

## Initialize Local App
- Install Amplify CLI
```bash
npm install -g @aws-amplify/cli
```
- Configure the Amplify CLI
```bash
amplify configure
```
- Initialize the Amplify App
(see [Initialize App](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-two/))
## Add Authentication
- Install amplify libraries
```bash
npm install aws-amplify @aws-amplify/ui-react
```
-  Create the authentication service
```bash
amplify add auth
```
- Deploy
```bash
amplify push --y
```
- Configure the React project with Amplify resources
```javascript
import { Amplify } from 'aws-amplify';
import config from './aws-exports';
Amplify.configure(config);
```
- Add auth in App.js
```javascript
import logo from "./logo.svg";
import "@aws-amplify/ui-react/styles.css";
import {
  withAuthenticator,
  Button,
  Heading,
  Image,
  View,
  Card,
} from "@aws-amplify/ui-react";

function App({ signOut }) {
  return (
    <View className="App">
      <Card>
        <Image src={logo} className="App-logo" alt="logo" />
        <Heading level={1}>We now have Auth!</Heading>
      </Card>
      <Button onClick={signOut}>Sign Out</Button>
    </View>
  );
}

export default withAuthenticator(App);
```
- Run app locally
```bash
npm start
```
![Alt text](/public/login.png?raw=true "Login Screen")

- Set up CI/CD of the FE and BE
(see [Set up CI/CD of the FE and BE](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-three/?e=gs2020&p=build-a-react-app-two))

- Deploy changes to live environment
``` javascript
git add .
git commit -m “added auth”
git push origin main
```
## Add API and Database
``` 
type Note @model @auth(rules: [ { allow: public } ] ){
  id: ID!
  name: String!
  description: String
  image: String
}
```
## Add storage
(see [Add Storage](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-five/))
## Final result:
![Alt text](/public/dashboard.png?raw=true "Home Screen")



This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).


Reference:
[Introduction: Build a Full Stack React App](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/)