# Maintenance

## Background

Maintained source fork: [0xble/plugins](https://github.com/0xble/plugins), branch `main`, of [openai/plugins](https://github.com/openai/plugins), upstream default `main`. Canonical checkout: `/Users/brianle/Repos/plugins`. Accepted upstream baseline: [0722921d5542fc593105c27bd52630babd8b8c2a](https://github.com/openai/plugins/commit/0722921d5542fc593105c27bd52630babd8b8c2a).

This fork is deliberately maintained against changes to the upstream curated plugin source. Publish fork upkeep only to `0xble/plugins`, never `openai/plugins`. This contract selects no installed plugin or active runtime.

## Preserve

- Keep upstream plugin behavior and catalog policy, with this source-upkeep contract as the fork-specific governance. A new plugin behavior divergence needs a separately accepted requirement and its own maintenance record, not an inferred local patch.
- Source adoption does not install, enable, authenticate or execute a plugin, app, MCP server, skill or hook. Those are separate consumer changes with separate authorization and proof.

## Update

Compare the accepted baseline with freshly fetched `upstream/main`. Adopt the latest upstream source into the maintained `main` through an owned-fork PR, retaining this contract. Review changed catalog sources and policies together with their affected plugin manifests and companion surfaces, using [README.md](README.md) as the repository layout authority. Inspect external catalog references as data, without cloning or executing their targets as part of source upkeep.

Record the newly accepted upstream revision in Background when adoption is verified. Before reporting `Updated` or `Already current`, fetch upstream again and require zero upstream-only commits. Otherwise report `Blocked` with the failed stage and exact refs.

## Verify

- Parse both `.agents/plugins/marketplace.json` and `.agents/plugins/api_marketplace.json`, plus affected plugin JSON, without loading their configuration. For each changed local catalog entry, require its source directory and `.codex-plugin/plugin.json` to exist and its catalog name to match the plugin manifest. Inspect changed URL and git-subdir entries for source and subdirectory changes without invoking them.
- Check affected manifests' local companion references against the accepted tree. Review changes to executable hooks, MCP endpoints, app bindings and skill content as source changes, not evidence of runtime compatibility.
- Require the source diff against freshly fetched `upstream/main` to contain only this contract or separately accepted, recorded divergence. After authorized publication, require maintained local and owned-remote `main` SHA parity.

```text
git rev-list --left-right --count upstream/main...main
```

The left count must be `0`. Catalog and manifest inspection proves source consistency only, not plugin installation, authentication or successful execution.
