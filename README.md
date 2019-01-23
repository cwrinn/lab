# git + <img src="https://user-images.githubusercontent.com/3167497/34473826-40b4987c-ef2c-11e7-90b9-5ff322c4966f.png" width="30" height="30"> = gitlab [![Build Status](https://travis-ci.org/zaquestion/lab.svg?branch=master)](https://travis-ci.org/zaquestion/lab) [![Go Report Card](https://goreportcard.com/badge/github.com/zaquestion/lab)](https://goreportcard.com/report/github.com/zaquestion/lab) [![codecov](https://codecov.io/gh/zaquestion/lab/branch/master/graph/badge.svg)](https://codecov.io/gh/zaquestion/lab) [![Join the chat at https://gitter.im/labcli](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/labcli) [![Donate](https://liberapay.com/assets/widgets/donate.svg)](https://liberapay.com/zaquestion/donate)

<p align="center"><img src="https://user-images.githubusercontent.com/1964720/42740177-6478d834-8858-11e8-9667-97f193ecb404.gif" align="center"></p>

Lab wraps Git or [Hub](https://github.com/github/hub), making it simple to clone, fork, and interact with repositories on GitLab, including seamless workflows for creating merge requests, issues and snippets.

```
$ lab clone gitlab-com/infrastructure

# expands to:
$ git clone git@gitlab.com:gitlab-com/infrastructure
```

## hub + <img src="https://user-images.githubusercontent.com/3167497/34473826-40b4987c-ef2c-11e7-90b9-5ff322c4966f.png" width="30" height="30"> = hublab??

lab will look for hub and uses that as your git binary when available so you don't have to give up hub to use lab
```
$ lab version
git version 2.11.0
hub version 2.3.0-pre9
lab version 0.14.0
```

# Inspiration

The [hub](https://github.com/github/hub) tool made my life significantly easier and still does! lab is heavily inspired by hub and attempts to provide a similar feel.

# Installation

Dependencies

* `git` or `hub`

### Homebrew
```
brew install zaquestion/tap/lab
```

### MacPorts
```
port install lab
```

### Scoop
```
scoop bucket add zaquestion https://github.com/zaquestion/scoop-bucket.git
scoop install lab
```

### Bash

Installs lab into `/usr/local/bin/`
```
curl -s https://raw.githubusercontent.com/zaquestion/lab/master/install.sh | bash
```

### PreBuilt Binaries

Head to the [releases](https://github.com/zaquestion/lab/releases) page and download your preferred release

### Source

Required
* [Go 1.11+](https://golang.org/doc/install)

```
git clone git@github.com:zaquestion/lab
cd lab
go install -ldflags "-X \"main.version=$(git  rev-parse --short=10 HEAD)\"" .
```

or

```
make install
```

### Tests
See the [contribution guide](CONTRIBUTING.md).

# Configuration

`lab` needs your GitLab information in order to interact with to your GitLab
instance. There are several ways to provide this information to `lab`:

1. Environment variables: `LAB_CORE_HOST`, `LAB_CORE_USER`, `LAB_CORE_TOKEN`
2. Environment variables: `CI_PROJECT_URL`, `CI_REGISTRY_USER`, `CI_JOB_TOKEN`
    - Note: these are meant for when `lab` is running within a GitLab CI pipeline
3. HCL config file: `./lab.hcl`
4. HCL config file: `~/.config/lab.hcl`

These are checked in order. If no suitable config values are found, `lab` will
prompt for your GitLab information and save it into `~/.config/lab.hcl`.
For example:
```
$ lab
Enter default GitLab host (default: https://gitlab.com):
Enter default GitLab user: zaq
Enter default GitLab token:
```

# Aliasing

Like hub, lab feels best when aliased as `git`. In your `.bashrc` or `.bash_profile`
```
alias git=lab
```

<p align="center"><img src="https://user-images.githubusercontent.com/2358914/34196973-420d389a-e519-11e7-92e6-3a1486d6b280.png" align="center"></p>
