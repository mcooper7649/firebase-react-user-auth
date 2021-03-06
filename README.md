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
4. now if we try to signup with two different passwords we should get our error
5. if we use the same pws we should get no error
6. lets add currentUser to our signup useAuth
7. we can put {currentUser} above our form
8. thats a json object so if we wanted to see what was inide of it we can JSON.stringiy(currentUser)
9. We will return our object with a propertie currentUser.email 
10. so we can replace with {curreentUser.email}
11. Also we want to only display when we have a currentUser so we can add {currentUser && curerntUser.email}

### setloading
---

1. Inside our Authcontext we need to configure setLoading(false)
2. This mean we have a user now and we are done loading
3. in our AuthProvider we can set the loading state ``   const [loading, setLoading] = useState(true);``
4. Now in our return we can add {!loading && children}
5. now we can remove the currentUser check from Signup.js
6. Don't forget to change the order of setCurrentUser on AuthContext.js


### Routing
---

1. Lets setup react-router next
2. npm i react-router-dom
3. lets go to app.js import { BrowserRouter as Router, Switch, Route } from 'react-router-dom'
4. Router will make the name easier to work with
5. Switch will determine which page we are currently on
6. Route will  determine which route on the page were going to

### Lets route our Signup Page
---

1. From app.js page let remove the Signup component
2. Then we can add Router Switch and Route
3. Route with a "/signup" path and component={Signup}
4. We can Wrap our Switch with our AuthProvider

```
function App() {
  return (
    <Container
      className="d-flex align-items-center justify-content-center"
      style={{ minHeight: "100vh" }}
    >
      <div className="w-100" style={{ maxWidth: "400px" }}>
        <Router>
          <AuthProvider>
            <Routes>
              <Route path="/signup" element={<Signup/>} />
            </Routes>
          </AuthProvider>
        </Router>
      </div>
    </Container>
  );
}
```


*REACT UPDATE*

1. In react-router-dom v6 Switch is repalced by routes "Routes"
2. import { Switch } is now { Routes }
3. component={Signup} is now element={<Signup/>} 



### Setup Home Route
---

1. Lets copy our route for signup and past above, for our / route
2. Lets replace 'signup' with '/'
3. lets add exact so you have to specifically go to '/'
4. Lets add the element {Dashboard} instead of Signup
5. RFC to create the new component Dashboard in component folder
6. put an h1 with just Dashbaord
7. Lets load the page to make sure it works.
8. Lets create the login route next
9. Copy and paste the signup route
10. rfc inside of components and create login component
11. inside app.js import login
12. copy and paste signup code into login component
13. replace the function name with login instead of signup
14. We can delete line 10 passwordConfirmRef as it won't be needed to login
15. remove the if sttatement for password confirmation
16. delete the final form group for pw confirmation too
17. Change the button text from Sign Up to Login
18. Change the h2 text to Log In
19. update bottom div text to 'need an account?'
20. Add Link To /signup page
21. import Link on the login.js page too



### Link to Login/Signup page
---

1. import { Link } from 'react-router-dom' on login page
2. add <Link to="/signup">Sign-Up</Link> so create an internal link route to our signup page
3. do steps 1 and 2 for login page
4. Now that we have our login pages confgured we can try to create an account
5. and then login w/ that account if no error, success
6. Lets use useHistory hook next on login.js
7. now after our successful login we can put history.push('/')

9. REACT UPDATE useHistory is deprecated. We use useNavigate now with navigate('/')
10. once you update the deprecated useHistory to useNavigate if we test our login with a new account we will be directed to the dashboard


### Setting up Dashboard
---


1. import { Card } from 'react-bootstrap'
2. Lets add a fragment
3. next well add a bootstrap card
4. then we can grab our div from our login page and paste it after our card
5. Update the div to have a Button to say Log out and add the variant style link
6. Also add an onClick event "handleLogout"
7. create the function handleLogout next we can leave it empty for now
8. lets impoort Button, Alert from react-bootstrap and useState hook from react
9. Lets copy the h2 and error checking from our login page paste into our dashboard Card.Body
10. change the h2 text to say profile, create a error hook with useState;
11. lets add ``<strong>Email: </strong>`` below our dashboard error checking
12. lets import Authso we can tap into our user ``import { useAuth } from "../contexts/AuthContext";``
13. Lets add a <Link> next to /update-profile and className="btn- btn-primary w-100 mt-3
14. link will have a text content of Update Profile
15. import Link from react-router-dom, hit save and we should have a undapte profile button


### Logout
---

1. if we want to logout we want to tap into useAuth(), lets add logout to our currentUser destructured functions const
2. lets add the logout function to AuthContext so we can use it.
3. lets create a new function called logout
4. it doesn't need to be passed any arguments
5. it will only have return auth.signOut();

logout function in AuthContext.js
```
  function logout() {
    return auth.signOut();
  }
```
6. We need to add logut to the const value so we can render it out
7. inside our Dashboard.js we can configurer our handleLogut() next
8. first lets setError('') so it clears any previous errors
9. add a try catch next
10. inside our catch we can setError('failed to logout')m so we know exactly why we failed
11. in our try, we can await logout()
12. after our await logout we can use the navigate fucntion react-router-dom
13. import it useNavigate and assisn a const navigate
14. everything looks like it works but you will notice if your logged out you get an eror cannot read property null of email, and see the actual code of the page
15. it mitigate this issue we need convert this route into a private route


### Lets create a PrivateRoute
---

1. Lets create a new component called PrivateRoute.js
2. rfc in the components folder.
3. This file is going to be a wrapper
4. we waant to pass an object into this function
5. component: Component, ...rest
6. import Route from react-router-dom
7. replace our div tags with Route
8. add { rest } to be passinto our Route
9. add render ={props => }
10. with a ternirary, for currentUser with the compoent and props if not redirect to login page

```
        <Route
           {...rest}
           render={props => {
            currentUser ? <Component {... props} /> : <Redirect to="/login" />
            }}>

        </Route>
```

11. Now we can add a the PrivateRoute component to our App.js for the "/" route