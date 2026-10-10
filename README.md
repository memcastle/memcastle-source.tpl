# MemCastle source module template

This GitTPL repository creates a source module with its own source identity, WIT contract and Rust component.
It is usable on its own and as a pinned child of `memcastle-plugin.tpl` once GitTPL composition is available.

```sh
git tpl --json questions https://github.com/memcastle/memcastle-source.tpl
git tpl init https://github.com/memcastle/memcastle-source.tpl my-source --init --answer module_name=my-source --defaults --strict-answers --json
```

The module is inert until its containing plugin is installed and the source is enabled.
The WIT contract is the version shipped with MemCastle 0.4; update it deliberately when the host contract changes.
