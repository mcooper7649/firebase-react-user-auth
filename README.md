# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

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

### `yarn build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)


# User Authentication with React and Firebase

  
  ## Web Dev Simplified
  
* [Link-To-Tutorial](https://www.youtube.com/watch?v=PKwu15ldZ7k)

## Steps to Setup
---

1. npx create-react-app
2. git init and first commit
3. Prep your readme.md
4. Go to firebase and create a new project
5. Enter Authorization Development and remove Google Analytics Features
6. enable sign in methods you want next
7. email + password
8. notice how authorized domains we have localhost as authorized. In production we will remove that.
9. Lets create the authorization Production next and follow steps 5-8 again
10. Remove localhost from Authorized domains
11. Switch back to development
12. Click on project overview from the left panel
13. click the </> icon to create a webapp and acquire the firebase API keys
14. Lets create .env.local file and add our api keys next
15. add the REACT_APP_FIREBASE_API_KEY, then add the rest following that same format
16. Next lets create firebase.js inside of src folder
17. then install firebase npm i firebase
18. import firebase from 'firebase/app'
19. import 'firebase/auth'


## Configuring our firebase.js file
---

1. Paste our api keys that we got from firebase into a const name app = firebase iniatlizeApp({})
2. Next we need to replace the values with the process.env.REACT_APP_FIREBASE_API_KEY and do that for the rest
3. Next we can export app as default, this allows us to use firebase throughout our application
4. We can also export the const auth = app.auth() to let us authenticate

## Preparing our files and installing packages
---

1. npm i bootstrap react-bootstrap
2. lets remove css and test files too and clean up our default directory next
3. inside our index.js remove the service worker and other deleted code references
4. Inside our App.js lets remove all the code inside the function and uneeded imports. return "hello world"
5. lets create a components folder inside src next
6. drag our app into that components folder
7. if we do npm start now it should load up our page


## Creating Signup.js component next
---

1. Inside components folder add Signup.js
2. Install es7 react snippets if you dont have the extension inside vscode already installed
3. type rfc inside your signup.js file and the extension should automatically generate a functionaly component
4. Inside our function return a fragment
5. Then a Card
6. Inside our Card we will return a div
7. w-100 text-center mt-2 will be the bootstrap classes
8. Inside our Card we can add a Card.Body above our div
9. Add an h2 with Sign up
10. Add our Form next
11. Form Group id = email
12. Form Label  email is the text
13. Form Control type = email, required, ref = {emailRef}
14. Copy the form group and paste it twice so we can make password field and confirm password fields
15. Then we can replace email with password and password confirm for our id, label, type and ref
16. Lets add a Button with type submit "Sign Up" as the text
17. lets add the class w-100 to make the width span the entire width of hte page
18. Now we have the form created on our SigUP component we can export and add to our app.js
19. We get errors says our Refs are defined. So lets do that on signup
20. lets import our useRef hook from react
21. declare const for each error and set to useRef();
22. Our form should show now but we need to setup our bootstrap so our styles will show


### Styling our Form
---

1. import ``import 'bootstrap/dist/css/bootstrap.min.css'
`` in your index.js
2. Lets add a container in our App.js to wrap our form
```
    <Container
      className="d-flex align-items-center justify-content-center"
      style={{ minHeight: "100vh" }}
    >
      <div className="w-100" style={{ maxWidth: "400px" }}>
        <Signup />
      </div>
    </Container>
```

### Adding Authorization
---

1. We want to add context because we want to access our user anywhere in our application
2. create a  contexts folder inside our src folder
3. create an AuthContext.js file inside
4. rfc and create the function, but remove default
5. rename the function to AuthProvider
6. Now lets create a const AuthContext = React.createContext(); above our function
7. Now we can use this context inside of our provider
8. We can also take the prop object {children} in our AuthProvider and render inside the AuthContext.Provider

```
const AuthContext = React.createContext();

export function AuthProvider({ children }) {
    return (
        <AuthContext.Provider>
            {children}
        </AuthContext.Provider>
    )
}
```

9. Next we can create the function useAuth and return useContext(AuthContext)
10. lets add a value prop to our AuthProvider function next. 
11. we have to create the const value = currentUser
12. Inside our AuthProvider we can create a currentUse hook with useState
13. ``  const [currentUser, setCurrentUser] = useState();``


### Connecting Firebase
---

1. import import { auth } from "../firebase";
2. lets createa  a signup function inside AuthProvider
3. it will take email, password arguments
4. it will ``return auth.createUserWithEmailAndPassword(email, password)
``
5. we can use auth.onAuthStateChanged(user){} to set our user
6. But we only want to do this once, so we will use the useEffect hook
7. make sure to add the [] so it will only run once

```
import React, { useContext, useState, useEffect } from "react";
import { auth } from "../firebase";

const AuthContext = React.createContext();

export function useAuth() {
  return useContext(AuthContext);
}

export function AuthProvider({ children }) {
  const [currentUser, setCurrentUser] = useState();

  function signup(email, password) {
    return auth.createUserWithEmailAndPassword(email, password);
  }

  useEffect(() => {
    auth.onAuthStateChanged((user) => {
      setCurrentUser(user);
    });
  }, []);

  const value = {
    currentUser,
  };

  return <AuthContext.Provider value={value}>{children}</AuthContext.Provider>;
}
```

8. lets add const unsubscribe in front of our auth.onAuthStateChange in the useEffect hook. It will remove the listener which is exactly what we want
9. now we can import useAuth into our signup.js component
10. const { signup } = useAuth();
11. Lets create a function handleSubmit() next for our submit handler
12. we can add the e arguemnt and preventDefault method()
13.  we can add the if ``if (passwordRef.current.value !== passwordConfirmRef.current.value){
        return setError('Passwords do not match')
    }``

14. Then the try  and we can put our sign up inside the try
15. Lets add async to the function as it will take time to grab this info
16. add await to the signup call
17. next we can add our catch block for any failures you may receive
18. now we can use setError('Failed to create an account');
19. Lets add a setError('') before our signup attempt to clear any errors
20. lets also setLoading(true)
21. after our catch we can then setLoading(false);
22. now we need to create our state for loading so it can be used in our prevous code
23. make the default loading state false
24. now in our form we can tie our onSubmit of the form tag to {handeSubmit}
25. In our button we can set the disable property = {loading} so it can't be submitted again while the form is loading.


### Adding the Error Alerting
---


1. we can add ``{error && <Alert variant="danger">{error}</Alert>}
``
2. This will display errors on submission with the variant danger
3. import it from react-bootstrap