# Troubleshooting

This section describes problems and solutions we encountered building and operating a parachain.

### The relay chain is not producing new blocks&#x20;

If you can't see the relay chain or parachain producing new blocks, check the logs of your commands.

Make sure that both validator nodes are running because if only one is running no new blocks will be produced.

Also double-check that you changed the `<ALICE_NODE_ID>` in the `--boot-nodes` command when running Bob. Otherwise, the Bob validator might not find Alice.&#x20;

#### macOS users

On macOS, it might help to temporarily disable the firewall in the system settings. This way you are not required to use the `--boot-nodes` parameter and the validator and collator nodes should be able to find each other without it.

### The parachain is not producing new blocks

Check if the relay chain validators are producing new blocks. If they are, check if the parachain is registered in the parachains tab.&#x20;

### Error: "Unexpected epoch change"

If you see something like `Error with block built on 0x...: ClientImport("Unexpected epoch change")` the easiest solution is to delete the files in the temporal directory.&#x20;

The directory you have to delete is indicated with `--base-path` in the previous command blocks. By default it would be `/tmp/relay/` so you would do `rm -rf /tmp/relay`

## Issues with clang and wasm on Mac with M1

Unfortunately, having issues with compiling substrate chains on computers with an Apple Silicon chip is quite common. When trying to `cargo build` your chain, you might encounter errors mentioning `clang` or `wasmtime-runtime`. This is because the built-in clang compiler on macOS does not really support wasm compilation.

In the following, we describe one way to make it work on a Mac running an M1 chip. The first set of steps is trying to make it work with the 'normal' binaries. If these do not fix the issue, we fall back to the intel binaries.&#x20;

### Silicon binaries

1. Follow the steps in the official substrate [installation instructions](https://docs.substrate.io/install/macos/) to install the required components.&#x20;
2. Run `brew install llvm`
3. Run `cargo install wasm-pack`
4. Set environment variables to point to the llvm installation of brew. \
   `export AR=/opt/homebrew/opt/llvm/bin/llvm-ar` \
   `export CC=/opt/homebrew/opt/llvm/bin/clang`\
   Consider adding these to your shell environment (e.g.  `~/.zshrc`) so that they are also set when rebooting your computer.
5. Check if the compilation now works. If it still does not, reboot your computer and try again. Don't forget to `cargo clean` before trying to recompile.

### Intel binaries

If you still have the same issue after following the instructions for installing the proper silicon binaries, try the following steps to install brew and llvm with the intel binaries instead. To do this, we install a second version of `brew` that is configured for intel binaries. The steps are taken from [this](https://medium.com/mkdir-awesome/how-to-install-x86-64-homebrew-packages-on-apple-m1-macbook-54ba295230f) guide.&#x20;

```
# Download the brew tarball
cd ~/Downloads
mkdir homebrew
curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
# Move it to another location
sudo mv homebrew /usr/local/homebrew

# Export path in zshrc
echo "export PATH=$HOME/bin:/usr/local/bin:$PATH" >> ~/.zshrc
echo "alias axbrew='arch -x86_64 /usr/local/homebrew/bin/brew'" >> ~/.zshrc
```

You can now install packages with `axbrew install package-name`.  So to install llvm and cmake, use

```
axbrew install llvm cmake
```

&#x20;You now need to set different environment variables. Use:

```
export AR=/usr/local/homebrew/opt/llvm/bin/llvm-ar
export CC=/usr/local/homebrew/opt/llvm/bin/clang
```

and now retry the compilation with `cargo build`. If this fixed the errors, consider adding the env variables to your shell environment with:

```
echo "export AR=/usr/local/homebrew/opt/llvm/bin/llvm-ar" >> ~/.zshrc
echo "export CC=/usr/local/homebrew/opt/llvm/bin/clang" >> ~/.zshrc
```
