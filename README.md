# MemCastle source module template

This GitTPL repository creates a source module with its own source identity, WIT contract and Rust component.
It is usable on its own and as a revision-tracked child of `memcastle-plugin.tpl` with GitTPL 0.14 composition.

```sh
git tpl --json questions "$PWD"
git tpl init "$PWD" ../my-source --init --answer module_name=my-source --defaults --strict-answers --json
```

Use `https://github.com/memcastle/memcastle-source.tpl` for a project shared beyond this machine;
GitTPL keeps the source location selected at init and does not replace a local path automatically.

The module is inert until its containing plugin is installed and the source is enabled.
The WIT contract is `memcastle:source@0.5.0`, matching Core's Rust 1.100 / WASI 0.3 migration.
Requires Rust 1.100+, the `wasm32-wasip3` target, wasm-tools 1.263.0, Python 3.11+, and migrated development Core.
Use Core commit `828f0f6` or a descendant (Wasmtime 50.0.3); stable 0.5.2 predates the migration.
Development currently reports 0.5.2 too, so the transitional `>=0.5, <0.6` default cannot distinguish those builds.
Tighten that range when the first compatible stable release is published.
Run `memcastle source test my-source` against the generated conformance fixture after installing a compatible Core CLI.

```sh
rustup target add wasm32-wasip3
TEMPLATE_ROOT="$PWD" git tpl test --json
```

The standalone and nested fixtures format, lint, build and validate components, then run the incremental fixture
through Core's actual WASI 0.3 host.
CI records the tested development Core SHA.
