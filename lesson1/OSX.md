# Installing the Anykey Toolchain on OSX.

## make, gcc

Chances are, you already have these installed. In case you don't there
are a number of options:

* install XCode via the AppStore
* use macports:
  * `port` packages are named `gmake` and `gcc48`
  * `homebrew` doesn't seem to support either gnu make or gcc ... go figure


## git

In case you don't have git installed, follow the instructions [here](http://git-scm.com/book/en/Getting-Started-Installing-Git)

## Install the ARM compiler

Either use macports:

    $ port install arm-none-eabi-gcc

Alternatively, download the mac packages from
[launchpad](https://launchpad.net/gcc-arm-embedded/+download) (homebrew
doesn't support the arm compiler either...), unpack the the archive in a
convenient location:

    $ mkdir compiler
    $ cd compiler
    $ tar -xjf $DOWNLOAD_LOCATION/gcc-arm-none-eabi-4_7-2013q2-20130614-mac.tar.bz2

and add the `bin` directory to your `$PATH` variable:

    $ export PATH=$PATH:`pwd`/gcc-arm-none-eabi-4_7-2013q2/arm-none-eabi/bin/

You'll need to edit the $PATH variable everytime you start a new
console, consider adding the PATH adjustment to your `.profile` ... 

You may need to change the commands above in case you're using a newer
version of the tools and the files aren't called
`gcc-arm-none-eabi-4_7-2013q2-20130614`

## Checkout out the SDK

Create a convenient working directory and check out the SDK

     $ mkdir anykey; cd anykey
     $ git clone https://github.com/anykey0xde/anykey-sdk.git

## make checksum and add it to your PATH

Just one more thing... We need a small utility to adjust the firmware we
compile for the LPC1343. Change into the `checksum` directory and run
make:

    $ cd anykey/anykey-sdk/checksum
    $ make

 Make sure the executable works, it should issue an error:

     $ ./checksum
     syntax: checksum <firmware.bin>

 Finally, add it to your PATH

     $ export PATH=$PATH:`pwd`

## Check everything works

Change into the `examples/blink` directory. Blinking LEDs are the
HelloWorld of embedded programming! You should just be able to run
`make` and the firmware should be created.


CONGRATULATIONS! the hardest part is behind you...