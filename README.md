# Reddit /r/place 2022 headless bot

This headless Python bot will automatically login to reddit, obtain access 
tokens (and refreshes them when they expire), obtain orders from the C&C server
and automatically place pixels at the desired locations.

## Requirements

- Python >= 3.8
- NumPy
- Matplotlib
- Rich
- aiohttp
- tomli

## Installation & updating to a new version

```bash
pip install --force git+https://github.com/PlaceNL/rPlace2022.git
```

## Docker image

For people experienced with Docker, there's also a docker image you can run:

```bash
docker run -t --pull=always --restart unless-stopped ghcr.io/placenl/placenl-python -u 'USERNAME' 'PASSWORD'
```

## Usage

### Linux / macOS

```bash
PlaceNL -u 'USERNAME' 'PASSWORD'
```

The bot supports multiple users:
```bash
PlaceNL -u 'USERNAME1' 'PASSWORD1' -u 'USERNAME2' 'PASSWORD2'
```

**IMPORTANT**: On macOS/Linux, use single quotes, otherwise your shell might 
interpret special characters. 

### Windows

On Windows, docker is probably the easiest way. 

1. Install [Docker Desktop](https://docs.docker.com/desktop/windows/install/).
2. Docker requires Windows Subsystem for Linux, so install that too.
3. Docker requires a kernel update for WSL, install from here: 
   https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package.
   Only step 4.1 is required.
4. Open PowerShell and run the above listed Docker command, but use double quotes instead of 
   single quotes (or specify a path to a config file, described below).
   
   ```bash
   docker run -t --pull=always --restart unless-stopped ghcr.io/placenl/placenl-python -u "USERNAME" "PASSWORD"
   ```
5. It should be up and running! It will also automatically restart in case of a rare crash.

### Specifying users in a config file

Besides specifying the username and password combinations on the command line, it's also possible to specify them
in a TOML config file. TOML is an INI-like file format, see the `config-example.toml` for an example.

To specify the path to the config file, add the `--from-config` flag (shorthand: `-c`):

```bash
PlaceNL --from-config config.toml
```

If using Docker, you'll need to give the container access to your files, otherwise it won't be able to find your 
config.toml file. So use `cd` to navigate to the directory with your config file, and run the following command:

**Linux/macOS**:

```bash
docker run -t --pull=always --restart unless-stopped -v $(pwd):/mnt ghcr.io/placenl/placenl-python -c /mnt/config.toml
```

**Windows (powershell)**:

```powershell
docker run -t --pull=always --restart unless-stopped -v ${PWD}:/mnt ghcr.io/placenl/placenl-python -c /mnt/config.toml
```
