# Linux hooking engine armhook
**armhook** is a Linux hooking engine for the ARM architecture. It allows to hook a function of a given process at a given address. The function prolog is properly saved and the hooked function can be continued after the hook handler has finished its work, but it can also be skiped. Everything is still in development, some features aren't implemented yet.

## Getting the code
The project consits of multiple repositories, to manage those you need [repo](http://source.android.com/source/downloading.html#installing-repo)

After installing **repo** clone this repository and run the following commands inside the directory:
```
$ repo init -u https://github.com/jhector/armhook.git
$ repo sync
```
This will fetch the code from the [armhook-core](https://github.com/jhector/armhook-core) repository as well as the code for the dependecies ([jansson](https://github.com/akheron/jansson))

## Building the code
So far, I only worked on the flame device running FirefoxOS. It hasn't been tested using different platforms.

### flame
In your B2G root folder is a directory called **system**, inside it, create a symlink to the location where you cloned this repository.
```
$ ln -s /path/to/this/repository /path/to/B2G/system/<symlink name>
```
After this step is completed, you can use the FirefoxOS build system to compile the code. The engine consists of two parts:
  * **armhook** - the main engine executable
  * **libarmhook.so** - a helper library for setting up the hooks

You can build those by running the following commands from your B2G root directory:
```
$ ./build.sh armhook
$ ./build.sh libarmhook
```

After a successful build, you can then push the two files onto the device using [adb](http://developer.android.com/tools/help/adb.html)

## Usage
The hooks are configured using a JSON config, for further details see the readme of the [armhook-core](https://github.com/jhector/armhook-core) repository.
