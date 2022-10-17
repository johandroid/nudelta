<h1 style="text-align: center;"> νΔ / nudelta </h1>

> Note: This software is in EARLY ALPHA.

A (WIP) open-source alternative to the [Nuphy Console](https://nuphy.com/pages/nuphy-console) for the [Air75 Mechanical Wireless Keyboard](https://nuphy.com/collections/keyboards/products/air75) by reverse-engineering the keyboard's USB protocol.

What this has:
* Support for NuPhy Air75
* The ability to back up and dump keymaps to binary formats
* The ability to dump keymaps to a human-readable hex format
* Loading keymap modifications from a `.yml` configuration file
    * Includes modifying the key as well as adding meta/alt/ctrl/shift as modifiers

What this DOESN'T have:
* A GUI
    * Would like to make one but it would take too much time.
* Macros
    * Need to reverse engineer those.
* Support for Halo65/Air60
    * I don't have them.
* RGB Control
    * I don't need that, personally.

Only tested on Linux so far, but I hope to also port this to macOS.
## Requirements
* [libusb](https://github.com/libusb/libusb)

> Nudelta will not work in its current state on ppc64 or any big-endian architectures. 

### Build Requirements
* C++17 Compiler
* Cmake
* Python 3.6+ w/ Pyyaml

## Building
```sh
mkdir build
cd build
cmake ..
make -j$(nproc)
sudo make install
```

## Usage

### Load a custom profile

```sh
sudo nudelta -l ./donns_remap.yml
```

The configuration .yml file is simple: there's a top level object called "keys": which is a map of physical keys on the actual keyboard to their replacements:

```yml
keys:
    caps_lock: esc
```

See [example.yml](example.yml) for a profile and somewhat more detailed examples.

You can find a list of:
  * Replaceable keys in [res/air75_indices.yml](res/air75_indices.yml).
  * Replacement keycodes in [res/air75_keycodes.yml](res/air75_keycodes.yml).

### Reset keymap to default
```sh
sudo nudelta -r
```

## License
The GNU General Public License v3 or, at your option, any later version. Check '[License](/License)'.
