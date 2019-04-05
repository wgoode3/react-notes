## create-react-app

Now that we have gotten our feet wet using React and using JSX, we could really use a nice tool to set up our projects for us. We've also probably seen a warning in our console when we use the ```babel``` script link letting us know this will not be a suitable solution in a production environment. 

Enter [create-react-app](https://github.com/facebook/create-react-app). This tool does exactly what it sounds like it does, it creates react apps. 

We can install ```create-react-app``` using the following command (assuming npm is installed)...

```shell
npm i -g create-react-app
```

You will need to use ```sudo``` if you get errors relating to permissions on MacOS or GNU/Linux.

When we go to run this, we can invoke ```create-react-app``` directly in the command line to make our app, however this has been a very slow process (sometimes longer than 3 minutes) each time we make an app in react.

```shell
create-react-app my-app
```

 To speed this up we can use [Yarn](https://yarnpkg.com/en/docs/install). Follow the instructions to install it, then we can use it to make ```create-react-app``` run a lot faster.

```shell
yarn create react-app my-app
```

However we choose to run ```create-react-app```, it will create a folder structure that looks like the following.

```
├─ my-app
┊ ├─ node_modules
┊ ├─ public
┊ ┊ ├─ favicon.ico
┊ ┊ ├─ index.html
┊ ┊ ├─ manifest.json
┊ ├─ src
┊ ┊ ├─ App.css
┊ ┊ ├─ App.js
┊ ┊ ├─ index.css
┊ ┊ ├─ index.js
┊ ┊ ├─ serviceWorker.js
┊ ├─ package.json

# some files and folders removed for brevity
```

We can run the newly created ```my-app``` by changing directory into it, and telling npm to start the project.

```shell
cd my-app
npm start
```

This will run ```my-app``` in a test server on port 3000. When we modify the ```App.js``` file, we will see the changes reflected at ```localhost:3000``` automatically.