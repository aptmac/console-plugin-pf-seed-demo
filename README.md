# OpenShift Console Plugin: PatternFly React Seed Demo

## Idea

The purpose behind this repository is to see what is required (and if it is possible) to modify an existing React project such that it can function as a dynamic plugin for the OpenShift Console while maintaining it's ability to be a standalone application.

The idea here was to take the PatternFly React Seed project and add the necessary parts on-top of it that would allow it to run as a dynamic plugin. At the very least, this includes a `console-extensions.json`, and `"consolePlugin"` entry in `package.json` for running locally.

The first problem I encountered was that the PF seed application currently uses React 18, which caused some warnings mentioning an incompatibility with the version 17 required for plugins. For this reason I picked a commit `62e92b7`, which was the last PF seed commit before they migrated to 18.

This repository is kind of hacked and thrown together, but does work and is a nice starting point for seeing how an existing project can be modified to work as both a plugin and a standalone application. Using the regular `npm run start:dev` or `npm run build && npm run start` will serve the PF application as expected. For the plugin, `yarn run start-console` will start a local instance of the OpenShift console and then you can run `npm run start-plugin` to run the dynamic plugin. At the moment I have the plugin running both as it's own Perspective, and as a section under the Admin portion of the Console.

## Commands
```sh
# Install development/build dependencies
npm install
```

### OpenShift Dynamic Plugin
```sh
# Start the OpenShift Console locally at localhost:9000
yarn run start-console

# Run the project as a dynamic plugin, and serve components at localhost:9091
npm run start-plugin
```

### Regular React & PatternFly application
```sh
# Start the development server at localhost:9096
npm run start:dev

or

# Run a production build (outputs to "dist" dir)
npm run build

# Run the "production" server at localhost:8080
npm run start
```
## Screenshot
![screenshot](https://github.com/aptmac/console-plugin-pf-seed-demo/assets/10425301/42e46134-80b3-40a0-ae33-905ed68c1f57)

Regular React application on the left, OpenShift Console on the right
