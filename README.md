# ZcashExplorer

This is a fork of https://github.com/nighthawk-apps/zcash-explorer, intended to
help develop support for block explorers in
[Zebra](https://github.com/ZcashFoundation/zebra).

## Local Dev Setup

### Build and run `zcashd`

``` shell
sudo pacman --noconfirm -S make git autoconf libtool unzip python automake pkgconf patch wget binutils gcc
cd
git clone https://github.com/zcash/zcash.git
cd zcash
./zcutil/clean.sh
./zcutil/build.sh -j$(nproc)
mkdir -p ~/.zcash
touch ~/.zcash/zcash.conf
```

Put the following to your `~/.zcash/zcash.conf`:

```
rpcport=8232
rpcbind=127.0.0.1
rpcuser=nighthawkapps
rpcpassword=ffwf
txindex=1
experimentalfeatures=1
insightexplorer=1
testnet=1
```

Run `./src/zcashd` and wait until it syncs.

### Build and run the explorer

``` shell
sudo pacman --noconfirm -S make elixir gcc git npm inotify-tools
cd
git clone https://github.com/ZcashFoundation/zcash-explorer
cd zcash-explorer
mix deps.get
cd assets
npm install
cd ..
```

Run `iex -S mix phx.server`.

Visit http://localhost:4000.

## Documentation: 

https://nighthawkapps.gitbook.io/zcash-explorer/

### License
Apache License 2.0
