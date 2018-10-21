 
 GUI wallet for PetCoin.



### Features:
This wallet contains the basic functions required to manage your Petcoin assets:

* Wallet creation
  * Create new wallet
  * Import from private keys
  * Import from mnemonic seed
* Basic wallet operation
  * Open an existing  wallet
  * Display wallet address & balance
  * Display private keys/seed
  * Export private keys/seed
  * Transactions listing/sorting/searching
  * Display transaction detail
  * Export incoming, outgoing, or all transactions to csv file.
  * Incoming Transaction notification
  * Send Petcoin to single recipient address, allow to set payment id and custom fee. Provides address lookup from addressbook.
  * Perform wallet optimization by creating fusion transactions 
  * Provides utility to generate payment id and integrated address
* Address book
  * Add/Edit/Delete address entry (label/name, address and payment id)
  * Listing/sorting/searching existing entries
  * Allow to store same wallet address with different payment id
  * Autosave address after sending to new/unknown recipient
* Misc
  * Provides setting to set local or public node address
  * Option to use system tray (on closing/minimizing wallet)
  * Provides list of public nodes, fetch/updated daily from Petcoin-nodes-json repo.
  * Custom node address that is not on the list will be added/remembered for future use
  * Theme: Dark & Light Mode
  * [Keyboard shortcuts](docs/shortcut.md)


### Notes

Petwallet relies on `pet-service` to manage wallet container &amp; rpc communication.

Release installer & packaged archived includes a ready to use `pet-service` binary, which is unmodified copy Petcoin release archive.

On first launch, Petwallet will try to detect location/path of bundled `pet-service` binary, but if it's failed, you can manually set path to the `pet-service` binary on the Settings screen.

If you don't trust the bundled `pet-service` file, you can compare the checksum (sha256sum) against one from the official release, or simply download and use the binary from official Petcoin release, which is available here: https://www.petcoin.pt/downloads/ Then,  make sure to update your `pet-service` path setting.

### Download &amp; Run Petwallet

#### Windows:
1. Download the latest installer here: https://www.petcoin.pt/downloads/
2. Run the installer (Petwallet_install.exe`) and follow the installation wizard.
3. Launch Petwallet via start menu or desktop shortcut.



### Build
You need to have `Node.js` and `npm` installed, go to https://nodejs.org and find out how to get it installed on your platform.

Once you have Node+npm installed:
```
# first, download pet-service binary for each platform
# from Petcoin official repo
# https://www.petcoin.pt/downloads/
# extract the pet-service executable somewhere

# clone the repo
$ git clone https://github.com/javalopes/Petcoin-GUI-Wallet
$ cd Petcoin-GUI-Wallet

# install dependencies
$ npm install

# create build+dist directory
$ mkdir -p ./build && mkdir -p ./dist

# copy/symlink icons from assets, required for packaging
$ cp ./src/assets/icon.* ./build/

# build GNU/Linux package
$ mkdir -p ./bin/lin
$ cp /path/to/linux-version-of/pet-service ./bin/lin/
$ npm run dist-lin

# build Windows package
$ mkdir -p ./bin/win
$ cp /path/to/win-version-of/pet-service.exe ./bin/win/
$ npm run dist-lin

# build OSX package
$ mkdir -p ./bin/osx
$ cp /path/to/osx-version-of/pet-service ./bin/osx/
$ npm run dist-mac
```

Resulting packages or installer can be found inside `dist/` directory.