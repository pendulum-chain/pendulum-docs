---
description: This page is about issues we encountered when trying to build the chain.
---

# Troubleshooting - Chain compilation

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
