## Preface

Loom is a new game engine (first released around March, 2013) and consists of 3 main parts:

### LoomScript

This is a custom programming language that looks similar to ActionScript 3 and C#. It looks to have most of the bells and whistles you might look for in a modern language.

### Loom SDK

This is written in C++ and is compatible with many platforms (Windows, OS X, Android and iOS at this time). It depends on [Cocos2d-x](http://www.cocos2d-x.org/) for handling graphics.

### `loom` command line tool

This little tool will guide you through most of your everyday tasks such as:

* managing Loom SDK versions
* building/packaging binaries
* running a game locally and on external devices
* displaying the documentation

The good thing about the `loom` command line tool is that it is very much automated and quite smart. For example, when you first do a `loom new some_game` it will download the latest SDK version and create a basic file structure to get you started with development (much like what Ruby on Rails does).

This also means that you will spend a lot of time on the console.

> For the rest of the document, Loom refers to the SDK and `loom` refers to the command line tool.

Type `loom help` to get an overview of the functionality provided by this tool. Also `loom help [command]` will tell you more about each command.

## Installation

Straight forward. Just download the [Loom SDK](http://theengine.co/downloads) and install it.

Doing this gives you the `loom` command line tool and a `~/.loom/` folder to house SDKs and documentation for them as well as global setting.

## Documentation

Viewing the documentation is done by simply running `loom docs`.

If you are inside a Loom game project folder, you will be presented with the documentation for the version of the SDK that the project uses.

Anywhere else, `loom` will check for the latest SDK version and opens up your default browser on the documentation for that version. If the latest version has not been fetched previously, it will fetch it automatically prior to displaying the documentation.

> Right now the documentation of both Loom and Cocos2d-x looks pretty thin which means you will have a hard time dissecting what exactly each function you encounter in the examples does. Lot's of experimentation is in order.

### Tutorials

When viewing the documentation you will find some basic tutorials (look for them in the *Modules*) that demonstrate some of Loom's functionality in practice.

### Example projects

The first thing to do after installing the Loom SDK is to [download some examples](http://theengine.co/examples) and take a look at their code. This will give you a great overview of LoomScript's syntax and what Loom is capable of.

> Right now the examples are indispensable because of the lack of proper documentation and tutorials.

## First steps

### Creating a new project

First of all, open up a console. Most of the work will be done there. Change to a folder that will house all your projects/code (`~/Code` is a good enough place) and type `loom new GameName` where "GameName" is the name of your game.

This will create a folder `GameName/` with the following structure:

    GameName
    |-- assets
    |   |-- Curse-hd.fnt
    |   |-- Curse-hd.png
    |   |-- bg.png
    |   `-- logo.png
    |-- bin
    |-- icons
    |   |-- android
    |   |   |-- drawable-hdpi
    |   |   |   `-- icon.png
    |   |   |-- drawable-ldpi
    |   |   |   `-- icon.png
    |   |   `-- drawable-mdpi
    |   |       `-- icon.png
    |   |-- ios
    |   |   |-- Default.png
    |   |   |-- Icon-114.png
    |   |   |-- Icon-144.png
    |   |   |-- Icon-57.png
    |   |   `-- Icon-72.png
    |   `-- osx
    |       `-- Application.icns
    |-- libs
    |-- loom.config
    `-- src
        |-- GameName.ls
        `-- main.ls
        
The top-level items are as follows:

#### assets

Contains all your images, sounds, maps etc. Almost anything that is not code but gets loaded by code will go here.

#### bin

Here you will put scripts and binaries that handle stuff that `loom` does not care about. For example a script to add your company's badge to the iOS icon prior to building the iOS app would fit nicely here.

#### icons

These are the application icons that `loom build` will use for the various platforms.

#### libs

A good place to store external libraries. This might be code that you are not developing within this project like a proprietary physics engine or a even your own custom audio engine.

> These would be like gems for Ruby.

#### loom.config

Contains settings about your project like the SDK version and the app's id and name.

#### src

Your LoomScript code goes here.

> `main.ls` should not be messed with at the beginnnig.

### Running the game

    loom run
    
Yeap, that's it. `loom` will take care of downloading the SDK version (if it hasn't already done so) and build a fresh new binary to run. It will also boot up the *asset agent* have the binary connect to it for live reloading of assets.
        
## Version control

### Git

When creating a new Loom project with `loom new [name]`, it generates a `.gitignore` file as well. This makes it quite easy to get started with Git's version control:

    git init
    git add .
    git commit -m "New game project"

## Building/Packaging

### OS X

Just do a `loom build osx` on a game project folder and it will build and package the OS X application inside the `build/` folder.

For the application's icon it will use the icon `icons/osx/Application.icns`.

### Android

Simply `loom build android` on a game project folder.

The first time you try and run this command it will most probably complain for missing **Android SDK**. In case it does, you will have to either download and link it to Loom or let `loom` handle the whole process for you:

    loom android install