# How to Setup Your Dev Environment

The best means of getting started with Ark development is to spin up your local network, complete with 51 test delegates. Here we will show you how to do precisely that: we will cover the tools you will need to set up your testnet, along with how to use those tools to get your network up and running.

## Installation

The following development tools need to be installed on your machine to develop an application using Ark Core:

- [NodeJS.](https://nodejs.org/en/) As Ark Core is written exclusively in NodeJS, the server-side framework for JavaScript, installing Node is a necessity for core development.

- [Git](https://git-scm.com/). As the most popular version control software in existence, Git is a staple of many developer workflows, and Ark is no exception. Downloading Git will allow you to download the latest version of Ark Core, as well as update your local copy of Core to incorporate the latest code changes as they are released.

- [Docker](https://www.docker.com/). Docker is a container management tool that's rapidly becoming the industry standard. If you are unfamiliar with containers or why managing them is important, fear not: when you install Ark Core, a robust Docker setup is provided for you out of the box. However, to use that setup, you are going to need a Docker installation on your machine already.

- [Lerna](https://lernajs.io/). In Greek mythology, Lerna was the home of the hydra, a fearsome beast with many heads. In JavaScript land, Lerna is a library used to tackle JavaScript projects with many packages. With Lerna installed as a **global** dependency, you are empowered to be fearless in the face of large JavaScript projects with many moving parts — including Ark Core.

- [Yarn](https://yarnpkg.com/en/). Yarn is a package manager that seeks to build upon the foundation of Node's npm. Although yarn is not a strict requirement, in many cases it works faster and more elegantly than npm. Most Ark developers use yarn, and as such, you will see `yarn` commands often used throughout our documentation.

## Spinning Up Your First Testnet

With the above dependencies installed, you are all set to start your first testnet. Here are the steps to doing so:

1. Navigate to a directory where you want to install Ark Core. This could be in a `projects` folder, or an `ark` folder, or something else entirely — the choice is up to you. Just make sure that you're in this folder before installing Core.

2. Once in the directory that you have created, install Ark Core using Git:

```bash
git clone git@github.com:ArkEcosystem/core.git
```

3. Move inside the newly-created `core` directory.

4. Run `lerna bootstrap`. This command will install all necessary JavaScript dependencies to get you up and running with Ark Core.

5. Although we have now installed all required JavaScript dependencies, there are a couple more missing pieces that we will need to fill in to get our testnet running. In particular, Ark Core makes use of the database technology [PostgreSQL](https://www.postgresql.org/). Installing Postgres the traditional way can be somewhat cumbersome. Fortunately, Docker has our backs here, and we've got your back with Docker.

6. From `core`, navigate to `docker/testnet`.  From within this directory, run the following command: `docker-compose up -d postgres`. This will install Postgres with the necessary settings to work with Ark Core.

7. Return to the `core` directory.

8. From `core`, navigate to `packages/core`. This is the starting point for all Ark nodes, `relays` and `forgers` alike.

9. From `core/packages/core`, run the command `yarn full:testnet`.

### Network boot

This last command, `yarn full:testnet`, is where the magic happens. Let us do a quick walkthrough of what happens when this command is run:

1. The `full:testnet` command is run within `core`, which as of the time of writing executes the following command in `npm`: `cross-env ARK_ENV=test ./bin/ark start --config ./lib/config/testnet --network testnet --network-start`

2. As seen in the previous step, the `./bin/ark` file is called with the `start` command. That command looks like this:

```js
app
  .command('start')
  .description('start a relay node and the forger')
  .option('-t, --token <token>', 'token name', 'ark')
  .option('-n, --network <network>', 'token network')
  .option('-b, --bip38 <bip38>', 'forger bip38')
  .option('-p, --password <password>', 'forger password')
  .option('--network-start', 'force genesis network start', false)
  .action(async (options) => require('../lib/start-relay-and-forger')(options))
```

3. Based on this command config and the options passed by the `full:testnet` command, we can see that the network sets the `config` directory to `lib/config/testnet`, the `network` option to `testnet`, and the `network-start` option to `true`, which starts our testnet from scratch with a new genesis block.

4. The exported function from `lib/start-relay-and-forger` is loaded and called with the above options to start the network. Let us look at the function exported by `start-relay-and-forger.js`:

const container = require('@arkecosystem/core-container')

```js
/**
  * Start a node.
  * @param  {Object} options
  * @return {void}
  */
module.exports = async (options) => {
  await container.setUp(options, {
    options: {
      '@arkecosystem/core-p2p': {
        networkStart: options.networkStart
      },
      '@arkecosystem/core-blockchain': {
        networkStart: options.networkStart
      },
      '@arkecosystem/core-forger': {
        bip38: options.bip38,
        address: options.address,
        password: options.password
      }
    }
  })
}
```

5. We'll delve more into the inner mechanics of `core-container` [here](/guidebook/core/node-lifecycle.html#bootstrapping-our-container). For now, we are going to take a brief look at the `setUp` method, found in the `core-container` package:

```js
/**
  * Set up the container.
  * @param  {Object} variables
  * @param  {Object} options
  * @return {void}
  */
async setUp (variables, options = {}) {
  this.env = new Environment(variables)
  this.env.setUp()

  if (options.skipPlugins) {
    return
  }

  this.plugins = new PluginRegistrar(this, options)
  await this.plugins.setUp()
}
```

1. After setting up environment variables based on the passed-in configuration, all Core plugins are loaded using the `options` key of the second argument to `container.setUp`. You can find the installed plugins in the `plugins.js` file located in the `core` package at `lib/config/testnet`.

This last step is where the meat-and-potatoes of ARK Core is loaded. During this step, the Postgres database is set up, all ARK-specific tables and fields are migrated, the genesis block is created, 51 forging delegates are created and set up to forge blocks — all the blockchain goodness you would expect from of a fully-formed testnet.

A full walkthrough of the node setUp process will be accessible in the Guidebook shortly, and further posts in the tutorials will guide you through some of the most common functions you will want to perform with your testnet. However, by following the steps above, you will be up and running with your very own network.
