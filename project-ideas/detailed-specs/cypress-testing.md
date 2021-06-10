---
layout: page
title: Getting started with Cypress testing
permalink: /project-ideas/2021/detailed-specs/cypress-testing
tags: intermine, outreachy
---

Cypress is a JavaScript testing framework used to run interaction and end-to-end tests in an automated browser environment.
This is how we test the user interface [BlueGenes](https://github.com/intermine/bluegenes) which serves data from an InterMine server.

To make tests reproducible, we use a stripped down InterMine server called Biotestmine, which contains enough data to test all features
of BlueGenes, while not being too time-consuming to build. The Cypress tests are written to be run against a BlueGenes connected to a
Biotestmine server, both when running the tests locally and when they are automatically run as part of CI.

Because of this, there are 4 steps to getting started with Cypress testing. Firstly, you'll need to build a Biotestmine and run it
as your local InterMine server. Then, you'll build and run BlueGenes locally, pointed to your local Biotestmine. Once these are setup,
you can run the Cypress tests. Finally, you'll have to learn about Cypress so you can write your own tests!

## Step 1: Setting up a local Biotestmine

The instructions here will differ depending on your operating system. If you are experienced with using Linux (Ubuntu is one example of this)
or familiar with the terminal in Mac, this should make the process easier. If you use Windows, it will still be possible but expect the
setup process to be challenging, and don't give up! Start at the section below according to what operating system you're using.

### Windows users

The software you'll be running uses docker to containerize the build process so it doesn't mess with your system. We recommend Windows Subsystem for Linux and using docker inside your embedded Linux system.

- Install WSL by following the Manual Installation Steps: [Install Windows Subsystem for Linux (WSL) on Windows 10 - Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
- When selecting the Linux distro we recommend Ubuntu (use version 18.04 LTS if asked)

Once you have installed WSL and a Linux distro, you should have a terminal window where you can enter commands. Try typing `uname`
and press the `Enter` key, and it should return "Linux". While you're in the terminal, you should input the following commands to install dependencies we'll need later:

```
sudo apt update
sudo apt install openjdk-11-jdk leiningen nodejs npm python3-pip git xvfb libgtk2.0-0 libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2
```

Finally, you will need to install Docker desktop on your Windows machine and configure it for WSL 2. This can be done by following these steps: 
[Docker Desktop WSL 2 backend | Docker Documentation](https://docs.docker.com/docker-for-windows/wsl/)

You should now have everything you need to build Biotestmine. Continue with the [Building Biotestmine](#building-biotestmine) section.

### Mac users

The easiest way to setup all the software required is to use Homebrew, a terminal package manager for MacOS. Start by opening a terminal
which you can do by typing *terminal* into Finder. If you don't already have Homebrew, paste the following code into the terminal and press
the `Return` key.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once Homebrew is available, start installing dependencies by running the following commands one at a time:

```
brew cask install docker
brew install docker-compose openjdk@11 leiningen node python@3.7 git
```

You should now have everything you need to build Biotestmine. Continue with the [Building Biotestmine](#building-biotestmine) section.

### Linux users

Type the following commands to install dependencies:

```
sudo apt update
sudo apt install openjdk-11-jdk leiningen nodejs npm python3-pip git xvfb libgtk2.0-0 libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2
```

Follow **steps 1 and 2** from: [How To Install and Use Docker on Ubuntu 18.04 - DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04#step-1-%E2%80%94-installing-docker)  

Follow **step 1** from: [How To Install Docker Compose on Ubuntu 18.04 - DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04#step-1-%E2%80%94-installing-docker-compose)

Continue to the [Building Biotestmine](#building-biotestmine) section directly below.

### Building Biotestmine

We will be using [intermine_boot](https://github.com/intermine/intermine_boot) to build Biotestmine. This is a tool that's still in development,
and aims to automate building InterMine servers with a single command. Run the commands below to get started (building can take 10-30 minutes).

```
pip install intermine_boot
intermine_boot start local
```

The build process will require the downloading of many dependencies, some of which may time out if you experience network issues.
If it succeeds, you should be able to access [http://localhost:9999/biotestmine](http://localhost:9999/biotestmine) in your browser and see the old user interface
of InterMine (which BlueGenes is set to replace). If the output doesn't seem right, or you can't access Biotestmine in your browser,
retry by rerunning the second command above.

**Note:** Biotestmine will continue running in the background until you stop it with `intermine_boot stop local` (you should also run this after failures to clean up the containers). If you stop it,
you'll have to run the same *start* command again to build it from scratch. You will need to have Biotestmine running for the steps
below to succeed.

## Step 2: Starting BlueGenes

Well done reaching this step! The hardest part is finally over and the remaining steps should be a breeze in comparison. Start
BlueGenes connected to your local Biotestmine by running the following commands:

```
git clone https://github.com/intermine/bluegenes.git
cd bluegenes
npm install
lein biotestmine
```

The first time you run lein, it will download all its dependencies which should result in many lines of output. Once everything has been
downloaded, it will start building BlueGenes and finally run the server locally. It will tell you to open [http://localhost:5000/](http://localhost:5000/) once it's ready.
When you open that URL in your browser, you should see BlueGenes.

**Note:** BlueGenes will continue to run in the *foreground* until you either close the window, or input *Ctrl+C*. You should keep it running
until you're done with the Cypress tests.

## Step 3: Running Cypress tests

The final step is to run our existing Cypress tests, so that you can learn how they work and start writing your own.
You will need to open a new terminal window as BlueGenes will be running in the foreground of the current one.
In the new terminal window, run the following commands:

```
cd bluegenes
npx cypress run
```

This should run through all the tests and end by outputting a summary of the test results.

**Note:** Don't be surprised if some tests fail, especially if you do repeat runs, as some tests assume a fresh database.

You can also run Cypress in debug mode to see a browser with the tests being run.

```
DEBUG=cypress:* npx cypress open
```

In the new window, click one of the test filenames below *integration tests* to run them, or the *run all specs* button to the right.

## Step 4: Learning Cypress

You'll want to start by opening one of the existing Cypress test files in `cypress/integration/` under the *bluegenes* folder, using
your preferred code editor. The rest of this section will contain links to online resources to get started with Cypress. You should
consult these resources, try to understand the existing tests, modify them and experiment with new tests, to build up your knowledge.

This is quite a lengthy introduction, but you should at least skim it to become familiar with the concepts:  
[Introduction to Cypress - Cypress Documentation](https://docs.cypress.io/guides/core-concepts/introduction-to-cypress)

When you're writing Cypress testing code, you'll want to reference the API documentation to look up how to use specific features of the library:  
[Table of Contents - Cypress Documentation](https://docs.cypress.io/api/table-of-contents)

## Closing remarks

Hopefully you managed to reach this point without encountering too many hurdles. Feedback to improve this guide is greatly appreciated,
so if you experienced any issues or see ways things can be made easier, please contact the mentor that sent you here!
