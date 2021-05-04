This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.

Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.

You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.

See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.

It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes. Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Deploy to Github Pages

### Step 1: Add homepage to package.json

Open your `package.json` and add a `homepage` field for your project:

```
"homepage": "https://myusername.github.io/my-app",
```

This URL is the URL of your GitHub repository.

### Step 2: Install gh-pages and add deploy to scripts in package.json

Now, whenever you run npm run build, you will see a cheat sheet with instructions on how to deploy to GitHub Pages.

To publish it at `https://myusername.github.io/my-app`, run:

```
npm install --save gh-pages
```

Add the following scripts in your package.json:

```
"scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

The predeploy script will run automatically before deploy is run.

### Step 3: Deploy the site by running npm run deploy

Then run:

```
npm run deploy
```

### Step 4: For a project page, ensure your project’s settings use gh-pages

Finally, make sure GitHub Pages option in your GitHub project settings is set to use the gh-pages branch.

GitHub Pages doesn’t support routers that use the HTML5 `pushState` history API under the hood (for example, React Router uses `browserHistory`). This is because when there is a fresh page load for a url like `http://user.github.io/todomvc/todos/42`, where `/todos/42` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of `/todos/42`. If you want to add a router to a project hosted on GitHub Pages, here are a couple of solutions:

* You could switch from using HTML5 history API to routing with hashes. If you use React Router, you can switch to `hashHistory` for this effect, but the URL will be longer and more verbose (for example, `http://user.github.io/todomvc/#/todos/42?_k=yknaj`). [Read more](https://reactrouter.com/web/api/HashRouter) about implementing `<HashRouter>`.

* Alternatively, you can use a trick to teach GitHub Pages to handle 404s by redirecting to your `index.html` page with a custom redirect parameter. You would need to add a 404.html file with the redirection code to the `build` folder before deploying your project, and you’ll need to add code handling the redirect parameter to `index.html`. You can find a detailed explanation of this technique in [this guide](https://github.com/rafrex/spa-github-pages).

Deployment instructions from [React documentation](https://create-react-app.dev/docs/deployment/#github-pages).

## Learn More

You can learn more in the [Create React App documentation](https://create-react-app.dev/docs/getting-started/).

To learn React, check out the [React documentation](https://reactjs.org/).
