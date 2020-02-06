# Eclipse Open VSX Registry

[![Gitpod - Code Now](https://img.shields.io/badge/Gitpod-code%20now-blue.svg?longCache=true)](https://gitpod.io/#https://github.com/eclipse/openvsx)
[![Join the chat at https://gitter.im/eclipse/openvsx](https://badges.gitter.im/eclipse/openvsx.svg)](https://gitter.im/eclipse/openvsx)
[![CI](https://github.com/eclipse/openvsx/workflows/CI/badge.svg)](https://github.com/eclipse/openvsx/actions?query=workflow%3ACI)

Open VSX Registry is a [vendor-neutral](https://projects.eclipse.org/projects/ecd.openvsx/who) open-source alternative to the [Visual Studio Marketplace](https://marketplace.visualstudio.com/vscode). It provides a server application that manages [VS Code extensions](https://code.visualstudio.com/api) in a database, a web application similar to the VS Code Marketplace, and a command-line tool for publishing extensions similar to [vsce](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#vsce).

## Development

The easiest way to get a development environment for this project is to open it in [Gitpod](https://gitpod.io/).

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/eclipse/openvsx)

Click _Open Browser_ on port 3000 to see the running web application.

### cli

 * `yarn build` &mdash; build the library and `ovsx` command
 * `yarn watch` &mdash; watch (build continuously)

The command line tool is available at `cli/lib/ovsx`.

### webui

 * `yarn build` &mdash; build the library
 * `yarn watch` &mdash; watch (build continuously)
 * `yarn build:dev` &mdash; build the dev frontend (run webpack)
 * `yarn watch:dev` &mdash; run webpack in watch mode
 * `yarn start:dev` &mdash; start Express to serve the frontend on port 3000

 The Express server is started automatically in Gitpod. A restart is usually not necessary.

### server

 * `./gradlew build` &mdash; build and test the server
 * `./gradlew assemble -t` &mdash; build continuously (the server is restarted after every change)
 * `./gradlew runServer` &mdash; start the Spring server on port 8080

The Spring server is started automatically in Gitpod. It includes `spring-boot-devtools` which detects changes in the compiled class files and restarts the server.

### OAuth Setup

If you would like to test authorization through GitHub, you need to [create an OAuth app](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/) with a callback URL pointing to the exposed port 8080 of your Gitpod workspace. You can get it by printing a predefined variable in the "Server" terminal in Gitpod:

```
echo $GITHUB_CALLBACK_URL
```

Note that the callback URL needs to be updated on GitHub whenever you create a fresh Gitpod workspace.

After you created the GitHub OAuth app, the next step is to copy the _Client ID_ and _Client Secret_ into [Gitpod environment variables](https://www.gitpod.io/docs/environment-variables/) named `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` and bound to this repository.

With these settings in place, you should be able to log in by authorizing your OAuth app.

## License

[Eclipse Public License 2.0](https://www.eclipse.org/legal/epl-2.0/)