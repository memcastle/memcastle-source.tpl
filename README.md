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
The WIT contract is the version shipped with MemCastle 0.4; update it deliberately when the host contract changes.
Run `memcastle source test my-source` against the generated conformance fixture after installing a compatible Core CLI.
`git tpl test` checks standalone and nested renders; template CI also builds a standalone WASM component.
