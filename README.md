# EMQ X Release Hot Upgrade Tool

This tool helps upgrade/downgrade emqx between different versions.

## Release upgrade tutorial

1. Download the script to the emqx node:

   ```
   curl -O -L https://raw.githubusercontent.com/emqx/release-upgrade-tool/main/release-upgrade-tool.sh

   chmod +x ./emqx_release_tool

   ./emqx_release_tool version
   ```

2. Download and install the specified emqx release:

   ```
   ./emqx_release_tool install 5.0.1
   ```

3. Check the downloaded and installed releases:

   ```
   ./emqx_release_tool list local
   ```

## Usage

### Available commands

```
./emqx_release_tool

emqx_release_tool: upgrade/downgrade emqx between patch versions

usage: emqx_release_tool <command> [options ...]

  <command>       Command to be executed

Valid commands are:
  list            List available releases from emqx.io.
  download        Download the specified emqx release.
  install         Install the specified emqx release.
  uninstall       Uninstall the specified emqx release.
  delete          Delete emqx downloaded release package for an emqx release.
  migrate         Export and convert internal-data/config-files from
                  currently installed release to internal-data/config-files
                  that can be applied by target release.
  apply           Import existing internal-data/config-files to current
                  installed release.
  version         Print current version of this tool.
```

### ./emqx_release_tool list

```
usage: emqx_release_tool list <local|all>

Valid options are:

  all       List all available releases from emqx.io
  local     Show current installed/downloaded emqx releases
```

### ./emqx_release_tool download

Download the specified release from emqx.io

```
usage: emqx_release_tool download <ReleaseNumber>

  <ReleaseNumber>   The target release version number. e.g. 5.0.1
```

### ./emqx_release_tool install

Install the specified release. If the release has not been downloaded,
this command will download it first.

```
usage: emqx_release_tool install <ReleaseNumber>

  <ReleaseNumber>   The target release version number. e.g. 5.0.1
```

### ./emqx_release_tool uninstall

Uninstall the specified release.

```
usage: emqx_release_tool uninstall <ReleaseNumber>

  <ReleaseNumber>   The target release version number. e.g. 5.0.1
```

### ./emqx_release_tool delete

Remove the downloaded package for the specified release.

```
usage: emqx_release_tool delete <ReleaseNumber>

  <ReleaseNumber>   The target release version number. e.g. 5.0.1
```

### ./emqx_release_tool migrate

Export and convert internal-data/config-files from currently installed release to internal-data/config-files that can be imported by target release.

```
usage: emqx_release_tool migrate [--config-files] [--data=<all|rules|users>] <ReleaseNumber> <ToDir>

  --config-files    Migrate config files from current release version
                    to the target release version.
  --data            Export and then migrate emqx's internal data from
                    current release version to the target release version.
  <ReleaseNumber>   The target release version number.
                    e.g. 5.0.1.
  <ToDir>           Where the result files would go.
```

### ./emqx_release_tool apply

This will reload the config files and import all the internal data files from the given dir.

```
usage: emqx_release_tool migrate <FromDir>

  <ToDir>           Where the config/data files should the tool read from.
```
