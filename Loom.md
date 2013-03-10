## Installation

Straight forward. Just download the [Loom SDK](http://theengine.co/downloads) and install it.

Doing this will install a `loom` command line tool that is responsible for lot's of tasks:

* managing Loom SDK versions
* building/packaging binaries
* running a game locally and on external devices
* displaying documentation

The good thing about the `loom` command line tool is that it is very much automated. This means that when you first do a `loom new some_game` it will download the latest SDK version and create a basic file structure to help you begin development (much like what Ruby on Rails does).

## Documentation

Viewing the documentation is done by simply running `loom docs`.

If you are inside a game project folder (one created by `loom new`), you will be presented with the documentation for that specific version of the SDK.

If you are outside a game project folder, Loom will check for the latest SDK version and open up the browser on the documentation for that version. If the latest version has not been fetched previously, it will fetch it automatically prior to displaying the documentation.

## Version control

### Git

When creating a new Loom project with `loom new [name]`, it generates a `.gitignore` file as well. This means that a mere `git init && git add . && git commit -m "New game project"` is all you need to get started with Git's version control.

## Building/Packaging

### OS X

Just do a `loom build osx` on a game project folder and it will build and package the OS X application inside the `build/` folder.

For the application's icon it will use the icon `icons/osx/Application.icns`.