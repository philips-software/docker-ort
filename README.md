# docker-ort

![Build Docker images](https://github.com/philips-software/docker-ort/workflows/Build%20Docker%20images/badge.svg)
![repolinter](https://github.com/philips-software/docker-ort/workflows/repolinter/badge.svg)
[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)

# Docker images

This repo will contain docker images with _OSS Review Toolkit_

## Usage

Images can be found on [https://hub.docker.com/r/philipssoftware/ort/](https://hub.docker.com/r/philipssoftware/ort/).

```
docker run -v /workspace:/project philipssoftware/ort --info analyze -f JSON -i /project -o /project/ort/analyzer
```

## Content

The images obviously contains Tern, but also two other files:
- `REPO`
- `TAGS`

### REPO

This file has a url to the REPO with specific commit-sha of the build.
Example: 

```
$ docker run philipssoftware/ort:latest cat REPO
https://github.com/philips-software/docker-ort/tree/14ab374e0812ba03e32e5f2c81c7c9dfb8ef7958
```

### TAGS

This contains all the similar tags at the point of creation. 

```
$ docker run philipssoftware/ort cat TAGS
ort:latest ort:2020-10-07
```

You can use this to pin down a version of the container from an existing development build for production. When using `tern` for development. This ensures that you've got all security updates in your build. If you want to pin the version of your image down for production, you can use this file inside of the container to look for the most specific tag, the last one.

## Why

> Why do we have our own docker image definitions?

ORT does not release their product with versions / tags. We want to be able to always know exactly what we're using in our build pipelines.
By including [ORT](https://github.com/oss-review-toolkit/ort) as a git submodule, we pin the version down to a certain commit-sha.

That's why we want our own docker file definitions.

## Issues

- If you have an issue: report it on the [issue tracker](https://github.com/philips-software/docker-ort/issues)

## Author

- Jeroen Knoops <jeroen.knoops@philips.com>
- Timo van de Put <timo.van.de.put@philips.com>

## License

License is MIT. See [LICENSE file](LICENSE.md)

## Philips Forest

This module is part of the Philips Forest.

```
                                                     ___                   _
                                                    / __\__  _ __ ___  ___| |_
                                                   / _\/ _ \| '__/ _ \/ __| __|
                                                  / / | (_) | | |  __/\__ \ |_
                                                  \/   \___/|_|  \___||___/\__|  

                                                                 Infrastructure
```

Talk to the forestkeepers in the `docker-images`-channel on Slack.

[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)
