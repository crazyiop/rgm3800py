# rgm3800py

This tool has been tested to work under MacOS X, Linux and Windows with a
[RoyalTek RGM 3800 GPS data logger](http://www.royaltek.com/index.php/rgm-3800).  A user has informed me that it also works
with the [RoyalTek RBT 2300](http://www.royaltek.com/index.php/rbt-2300) device.

## Generally

The device must be turned on, it's not sufficient to plug it in.
If you get strange output or errors after playing around please unplug the
device and turn it off.  After plugging it in again and turning it on it
should behave correctly again.  In rare cases this isn't sufficient, you will
then need to unplug the logger and remove batteries for a short while. 

Run this tool in a terminal, this shows you some usage information:

```bash
./rgm3800.py --help
```

## Operating system specific requirements

### MacOS X

Please first install a PL2303 driver, e.g.:

* [Mac OS X Prolific PL2303 driver project](http://osx-pl2303.sourceforge.net/)
* [Prolific PL2303 Mac OS X download page](http://www.prolific.com.tw/US/ShowProduct.aspx?p_id=229&pcid=41)

Or you can install it with [brew-cask](https://github.com/phinze/homebrew-cask)

```bash
brew cask install prolific-usb-serial-driver
```

### Linux

Please install a kernel that supports the PL2303 USB-serial chip.
Just plug it in and have a look in your dmesg if the device is found.
In some cases the access to the device might be prohibited for the
unprivileged user. Installing `99-rgm3800.rules` to `/etc/udev/rules.d/`
should solve the problem. If this is not sufficient to get access to
the logger, you may also check whether you have a running and blocking gpsd
daemon in the background as a result of another udev rule (`99-gpsd.rules`).

### Windows

You will need a PL2303 driver, [Python](http://python.org/), `pywin32` and `pyserial`.

