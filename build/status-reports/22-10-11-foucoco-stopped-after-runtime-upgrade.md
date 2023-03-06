# 22-10-11 Foucoco stopped after runtime upgrade

On 22-10-11 we were experimenting with runtime upgrades on Rococo. One of the upgrades contained a Polkadot version bump from v0.9.24 to v0.9.29.

Shortly after the upgrade the collators did not procuce blocks anymore and showed the following error message

```
2022-10-10 23:12:54 Starting collation. relay_parent=0xd3e97359dc10367e1ba4e20f2430a7b5f413b40d3da24ab3c53611003a8a510d at=0xabaa17a16008ef8d6152a0cf62f508a0f0abcaa236acb8b1d053421176c45c2f
2022-10-10 23:12:55 panicked at 'Storage root must match that calculated.', /Users/torstenstueber/.cargo/git/checkouts/substrate-7e08433d4c370a21/cc370aa/frame/executive/src/lib.rs:528:9
2022-10-10 23:12:55 Block prepare storage changes error: Error at calling runtime api: Execution failed: Execution aborted due to trap: wasm trap: wasm `unreachable` instruction executed
WASM backtrace:
    0: 0x2e2e3b - <unknown>!rust_begin_unwind
    1: 0x2a7720 - <unknown>!core::panicking::panic_fmt::h8b1b9291c42fd987
    2: 0xe98bb - <unknown>!frame_executive::Executive<System,Block,Context,UnsignedValidator,AllPalletsWithSystem,COnRuntimeUpgrade>::execute_block::h42c3d25f5aa45dec
    3: 0x23fd38 - <unknown>!Core_execute_block
2022-10-10 23:12:55 :broken_heart: Error importing block 0x44244ec8162b9672f82308689442f9e192d19fb090402a08a3139affa1292ee7: consensus error: Import failed: Error at calling runtime api: Execution failed: Execution aborted due to trap: wasm trap: wasm `unreachable` instruction executed
WASM backtrace:
    0: 0x2e2e3b - <unknown>!rust_begin_unwind
    1: 0x2a7720 - <unknown>!core::panicking::panic_fmt::h8b1b9291c42fd987
    2: 0xe98bb - <unknown>!frame_executive::Executive<System,Block,Context,UnsignedValidator,AllPalletsWithSystem,COnRuntimeUpgrade>::execute_block::h42c3d25f5aa45dec
    3: 0x23fd38 - <unknown>!Core_execute_block
2022-10-10 23:12:55 panicked at 'Storage root must match that calculated.', /Users/torstenstueber/.cargo/git/checkouts/substrate-7e08433d4c370a21/cc370aa/frame/executive/src/lib.rs:528:9
2022-10-10 23:12:55 Block prepare storage changes error: Error at calling runtime api: Execution failed: Execution aborted due to trap: wasm trap: wasm `unreachable` instruction executed
WASM backtrace:
    0: 0x2e2e3b - <unknown>!rust_begin_unwind
    1: 0x2a7720 - <unknown>!core::panicking::panic_fmt::h8b1b9291c42fd987
    2: 0xe98bb - <unknown>!frame_executive::Executive<System,Block,Context,UnsignedValidator,AllPalletsWithSystem,COnRuntimeUpgrade>::execute_block::h42c3d25f5aa45dec
    3: 0x23fd38 - <unknown>!Core_execute_block
2022-10-10 23:12:55 :broken_heart: Error importing block 0x44244ec8162b9672f82308689442f9e192d19fb090402a08a3139affa1292ee7: consensus error: Import failed: Error at calling runtime api: Execution failed: Execution aborted due to trap: wasm trap: wasm `unreachable` instruction executed
WASM backtrace:
    0: 0x2e2e3b - <unknown>!rust_begin_unwind
    1: 0x2a7720 - <unknown>!core::panicking::panic_fmt::h8b1b9291c42fd987
    2: 0xe98bb - <unknown>!frame_executive::Executive<System,Block,Context,UnsignedValidator,AllPalletsWithSystem,COnRuntimeUpgrade>::execute_block::h42c3d25f5aa45dec
    3: 0x23fd38 - <unknown>!Core_execute_block
```

This indicated that the local node needed an upgrade as well, which was unexpected: our assumption was that runtime upgrades do not require node upgrades.

Indeed we could fix the problem by upgrading the nodes also to the latest version v0.9.29.

**Learning**: for every new release of Polkadot we need to thoroughly read the release notes on GitHub. They will contain information whether a node upgrade is required as well.
