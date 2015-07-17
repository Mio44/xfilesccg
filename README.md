# The X-Files CCG module for ([GCCG](http://gccg.sourceforge.net/))

This is not a standalone program, it is an add-on module for the GCCG platform to allow online play of The X-Files CCG.
Also note that following the below steps will only allow you to run a client in offline mode.
That means you will be able to browse the cards and build decks, but you won't be able to trade cards or play the game.
For the latter, you need to connect your client to a game server, which currently is 

# Installation

The installation of the game client varies based on the platform of your system.

## Linux & Mac

You need to install the packages listed in the prerequisities. 
Then, you can choose either the binaries installation, or the source installation.

### Prerequisities

The following packages are required prior to installation. 
For installing from source, keep in mind that some Linux distributions (such as Ubuntu) require *-dev packages in order to install the headers for these libraries.

* sdl
* sdl_image
* sdl_net
* sdl_ttf
* sdl_mixer
* libjpeg
* libpng3

### Binaries

There are pre-built binaries available for the most common platforms.
Depending on your system, replace the `<platform>` placeholder in the following commands with one of `darwin-i386`, `linux-i386`, `linux-x86_64`.
Run the following commands, e.g. in your home directory:
```
mkdir gccg
cd gccg
wget http://gccg.bornano.fr/gccg/gccg-core-1.0.11.tgz
tar xzvf gccg-core-1.0.11.tgz
./gccg_package source add https://raw.githubusercontent.com/Mio44/xfilesccg/master/
./gccg_package update
./gccg_package install client fonts <platform> xf xf-cards
```

### Source

Run the following commands, e.g. in your home directory:
```
mkdir gccg
cd gccg
wget http://gccg.bornano.fr/gccg/gccg-core-1.0.11.tgz
tar xzvf gccg-core-1.0.11.tgz
./gccg_package source add https://raw.githubusercontent.com/Mio44/xfilesccg/master/
./gccg_package update
./gccg_package install client fonts source xf xf-cards
make all
```

### Running

To start the client, run `./Xf`.
To keep everything updated, run `./gccg_package update` while the game is not running.

## Windows

* Download and extract [The Windows Installer](http://gccg.sourceforge.net/downloads/gccg_install.zip) to your hard drive, e.g. to a folder called `gccg`.
* Run the following commands in the extracted folder:
```
perl gccg_package source add https://raw.githubusercontent.com/Mio44/xfilesccg/master/
perl gccg_package update
perl gccg_package install client fonts windows32 xf xf-cards
```
* To start the client, Run `Xf.bat`.
* To keep everything updated, run `Update Everything.bat` while the game is not running.

# Offline Mode

After starting the game, the client window opens. Note that you will be running the game client in offline mode.
That means you will be able to browse the cards and build decks, but you won't be able to trade cards or play the game.

* Press Ctrl+B to view the card collection. These are all the cards in the game.
* Press Ctrl+I to import one of the predefined decks.
* Press Ctrl+E to edit the active deck.
* For the steps to create your own deck from scratch, see (http://gccg.sourceforge.net/).

# Online Mode

To trade cards and play the game, you need to connect your game client to a game server.
You need to know the URL or IP address of the game server to do that.
Then, simply start the client with the following command:

* on Linux & Mac, use `./Xf --server <url/ip>`
* on Windows, use `Xf.bat --server <url/ip>`

Note: currently, no public game server exists.

# Server

To run your own game server on your PC, you need to install some additional modules. 
The server itself consists of 3 or more separate processes which you need to run:

* 1 factory server
* 1 meta server
* 1 or more table servers

## Linux & Mac

To install the server module, run the following commands in your game installation directory:

```
./gccg_package update
./gccg_package install server xf-server
```
To run the factory server, use the command `./ccg_server --load factory-server.triggers Xf.xml`.
To run the meta server, use the command `./ccg_server --load meta-server.triggers Xf.xml`.
To run a table for 1 player, use the command `./ccg_server --players 1 --bet 0 --rules Xf.rules --load server.triggers Xf.xml`.
To run a table for 2 players, use the command `./ccg_server --players 2 --bet 0 --rules Xf.rules --load server.triggers Xf.xml`.

## Windows

To install the server module, run the following commands in your game installation folder:

```
perl gccg_package update
perl gccg_package install server xf-server
```
To run the factory server, use the command `ccg_server.exe --load factory-server.triggers Xf.xml`.
To run the meta server, use the command `ccg_server.exe --load meta-server.triggers Xf.xml`.
To run a table for 1 player, use the command `ccg_server.exe --players 1 --bet 0 --rules Xf.rules --load server.triggers Xf.xml`.
To run a table for 2 players, use the command `ccg_server.exe --players 2 --bet 0 --rules Xf.rules --load server.triggers Xf.xml`.

## Connecting

If you have a game server running on your PC and want to connect the game client to it, you can launch it without the `--server` parameter.
The client automatically connects to a server running on the same PC.