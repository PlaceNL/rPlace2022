# Reddit /r/place 2022 headless bot

This headless Python bot will automatically login to reddit, obtain access
tokens (and refreshes them when they expire), obtain orders from the C&C server
and automatically place pixels at the desired locations.

## Requirements

- Python >= 3.8
- NumPy
- Pillow
- Rich
- aiohttp

## Installation

For now, just download the script and run it with Python. More easy installation methods will come soon.

## Usage

```bash

PlaceNL.py -u "USERNAME" "PASSWORD"
```


The bot supports multiple users:

```bash
PlaceNL -u 'USERNAME1' 'PASSWORD1' -u 'USERNAME2' 'PASSWORD2'
```

**IMPORTANT**: Use single quotes, otherwise your shell might interpret special characters.

## Docker image

For people experienced with Docker, there's also a docker image you can run:

```bash
docker run -t ghcr.io/placenl/placenl-python -u 'USERNAME' 'PASSWORD'

```
