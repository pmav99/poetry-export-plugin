---
title: "Export plugin"
draft: false
type: docs
layout: single

menu:
  docs:
    weight: 1001
---

# Export plugin

The export plugin allows the export of locked packages to various formats.

{{% note %}}
Only the `requirements.txt` format is currently supported.
{{% /note %}}

## Exporting packages

The plugin provides an `export` command to export the locked packages to
various formats.

The default export format is the `requirements.txt` format which is currently
the most compatible one. You can specify a format with the `--format (-f)` option:

```bash
poetry export -f requirements.txt
```

By default, the `export` command will export to the standard output.
You can specify a file to export to with the `--output (-o)` option:

```bash
poetry export --output requirements.txt
```

Similarly to the [`install`]({{< relref "../cli#install" >}}) command, you can control
which [dependency groups]({{< relref "managing-dependencies#dependency-groups" >}})
need to be exported.

If you want to exclude one or more dependency group from the export, you can use
the `--without` option.

```bash
poetry export --without test,docs
```

You can also select optional dependency groups with the `--with` option.

```bash
poetry export --with test,docs
```

{{% note %}}
The `--dev` option is now deprecated. You should use the `--with dev` notation instead.
{{% /note %}}

It's also possible to only export specific dependency groups by using the `only` option.

```bash
poetry export --only test,docs
```

### Available options

* `--format (-f)`: The format to export to (default: `requirements.txt`). Currently, only `requirements.txt` is supported.
* `--output (-o)`: The name of the output file.  If omitted, print to standard output.
* `--without`: The dependency groups to ignore when exporting.
* `--with`: The optional dependency groups to include when exporting.
* `--only`: The only dependency groups to include when exporting.
* `--default`: Only export the default dependencies.
* {{< option name="dev" deprecated=true >}}Include development dependencies.{{< /option >}}
* `--extras (-E)`: Extra sets of dependencies to include.
* `--without-hashes`: Exclude hashes from the exported file.
* `--with-credentials`: Include credentials for extra indices.
