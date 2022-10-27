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


# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
