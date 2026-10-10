# MemCastle source module template

This GitTPL repository creates a source module with its own source identity, WIT contract and Rust component.
It is usable on its own and as a pinned child of `memcastle-plugin.tpl` with GitTPL composition.

```sh
git tpl --json questions "$PWD"
git tpl init "$PWD" ../my-source --init --answer module_name=my-source --defaults --strict-answers --json
```

After publication, the template URL `https://github.com/memcastle/memcastle-source.tpl` replaces the local path.

The module is inert until its containing plugin is installed and the source is enabled.
The WIT contract is the version shipped with MemCastle 0.4; update it deliberately when the host contract changes.
Run `memcastle source test my-source` against the generated conformance fixture after installing a compatible Core CLI.
