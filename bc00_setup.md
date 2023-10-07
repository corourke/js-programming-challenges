### Challenge 0: Setting Up Your JavaScript Development Environment

This doc will guide you through setting up your JavaScript development environment for the rest of the challenge. The instructions are tailored for Mac OS users.

#### Step 1: Install Homebrew

Homebrew is a package manager for macOS that allows you to easily install software and packages.

To install Homebrew, open your Terminal and run the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, update Homebrew's list of formulae and packages:

```bash
brew update
```

#### Step 2: Install Node and npm

Node.js is a runtime that lets you execute JavaScript code server-side. npm (Node Package Manager) comes bundled with Node.js and allows you to install various packages.

Install Node.js and npm using Homebrew by running the following command:

```bash
brew install node
```

To verify the installations, you can run:

```bash
node -v
npm -v
```

Each of these commands should return a version number, confirming that the installation was successful.

#### Step 3: Install Git

Git is a version control system that helps you manage your code.

To install Git, run:

```bash
brew install git
```

To verify the installation, you can run:

```bash
git --version
```

This should return a version number, confirming that the installation was successful.

#### Step 4: Create a New Project Directory

Choose a location on your computer where you'd like to store your projects. 

A good practice is to create a directory within your home directory under which to put all your project directories. This keeps iCloud from backing up potentially large project directories. The backups aren't needed as we will generally keep copies of our files in GitHub. I usually create a directory called `dev` within my home directory.

To create this directory and navigate into it, run:

```bash
mkdir ~/dev
cd ~/dev
```

And then create a project directory here:

```bash
mkdir blockchain-js
cd blockchain-js
```

#### Step 5: Initialize the Node Project

Now that you're inside your project directory, let's initialize a new Node.js project.

Run the following command and follow the prompts:

```bash
npm init
```

When you run `npm init`, you're initializing a new Node.js project, which includes the creation of a `package.json` file. This file holds the metadata and dependencies for your project. 

After running this command, you will be prompted to answer several questions to set up your `package.json` file. Here's a breakdown of the questions:

1. **name**: The name of your package/project. This needs to be lowercase and one word, but can contain hyphens or underscores.
    - **Default**: The name of the current directory.
    - **Example Answer**: `blockchain-js`

2. **version**: The initial project version.
    - **Default**: `1.0.0`
    - **Example Answer**: `0.1.0`

3. **description**: A brief description of your project.
    - **Default**: Empty
    - **Example Answer**: `A simple JavaScript blockchain implementation`

4. **entry point**: The entry point file for your project, usually `index.js`.
    - **Default**: `index.js`
    - **Example Answer**: `app.js`

5. **test command**: The command that will be used to run tests for your project.
    - **Default**: Empty
    - **Example Answer**: `jest` (We'll be using Jest for testing.)

6. **git repository**: If your project is hosted on a Git repository, provide the URL here.
    - **Default**: Empty
    - **Example Answer**: `https://github.com/yourusername/my-blockchain-project.git`

7. **keywords**: Keywords related to your project. Useful for people searching for your project.
    - **Default**: Empty
    - **Example Answer**: `blockchain, javascript`

8. **author**: Your name or alias.
    - **Default**: Empty
    - **Example Answer**: `John Doe <jdoe@gmail.com`

9. **license**: The license your project will use.
    - **Default**: `ISC`
    - **Example Answer**: `MIT`

You can simply press `Enter` to accept the default values or provide your own. Once all questions have been answered, `npm` will generate a `package.json` file containing the information you provided.

Finally, you'll see a preview of your `package.json` and a prompt asking if it looks good. If everything appears correct, type `yes` and press `Enter`.

Your `package.json` file is now created and your Node.js project is initialized!

#### Step 6: Initialize Git Repository

Since Git is installed, you can initialize a new Git repository in your project directory.

Run the following command:

```bash
git init
```

This initializes a new Git repository and begins tracking an empty initial commit.git

#### Step 7: Install Jest as a Dev Dependency

Jest is a JavaScript testing framework that we'll use for writing unit tests.

To install Jest, run:

```bash
npm install --save-dev jest
```

Now, your development environment is all set up! You have Homebrew, Node.js, npm, Git, and Jest installed, and your project is initialized and ready to go. 


### Some essential Git

Great tutorials on Git can be found everywhere, but for now, if you aren't using the source control features in VS Code (or your editor of choice) there are two essential commands needed. 

First, create a file in your project directory called `.gitignore`. This file tells Git which files not to track. Use the sample file shown down below.  Don't worry that it's a long list, it is just covering a lot of potential configurations.

Now for the Git commands. 

Every so often, you want to execute these commands to save the current state of your project as a Git version. 

1 -- Add changed, added or deleted files to the 'staged' list:

```bash
% git add --all
```

2 -- Commit the staged files to a version:

```bash
% git commit -m "description of what has changed"
```

3 -- check Git status:

```bash
% git status
```

Add this file to your project directory:
`.gitignore`
```gitignore
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
lerna-debug.log*
.pnpm-debug.log*

# Diagnostic reports (https://nodejs.org/api/report.html)
report.[0-9]*.[0-9]*.[0-9]*.[0-9]*.json

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage
*.lcov

# nyc test coverage
.nyc_output

# Grunt intermediate storage (https://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# Bower dependency directory (https://bower.io/)
bower_components

# node-waf configuration
.lock-wscript

# Compiled binary addons (https://nodejs.org/api/addons.html)
build/Release

# Dependency directories
node_modules/
jspm_packages/
package-lock.json

# Snowpack dependency directory (https://snowpack.dev/)
web_modules/

# TypeScript cache
*.tsbuildinfo

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional stylelint cache
.stylelintcache

# Microbundle cache
.rpt2_cache/
.rts2_cache_cjs/
.rts2_cache_es/
.rts2_cache_umd/

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity

# dotenv environment variable files
.env
.env.development.local
.env.test.local
.env.production.local
.env.local

# parcel-bundler cache (https://parceljs.org/)
.cache
.parcel-cache

# Next.js build output
.next
out

# Nuxt.js build / generate output
.nuxt
dist

# Gatsby files
.cache/
# Comment in the public line in if your project uses Gatsby and not Next.js
# https://nextjs.org/blog/next-9-1#public-directory-support
# public

# vuepress build output
.vuepress/dist

# vuepress v2.x temp and cache directory
.temp
.cache

# Docusaurus cache and generated files
.docusaurus

# Serverless directories
.serverless/

# FuseBox cache
.fusebox/

# DynamoDB Local files
.dynamodb/

# TernJS port file
.tern-port

# Stores VSCode versions used for testing VSCode extensions
.vscode-test

# yarn v2
.yarn/cache
.yarn/unplugged
.yarn/build-state.yml
.yarn/install-state.gz
.pnp.*

.obsidian
```