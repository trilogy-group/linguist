
# Linguist Development with DF Devspaces

## Install DF Devspaces

1. Create and install devspaces client as it is written in help guide https://support.devspaces.io/article/22-devspaces-client-installation.

2. Here is some details about DF Devspaces https://devspaces.io/devspaces/help

Here follows the main commands used in Devspaces cli. 

|action   |Description                                                                                   |
|---------|----------------------------------------------------------------------------------------------|
|`devspaces --help`                    |Check the available command names.                               |
|`devspaces create [options]`          |Creates a DevSpace using your local DevSpaces configuration file |
|`devspaces start <devSpace>`          |Starts the DevSpace named \[devSpace\]                           |
|`devspaces bind <devSpace>`           |Syncs the DevSpace with the current directory                    |
|`devspaces info <devSpace> [options]` |Displays configuration info about the DevSpace.                  |

Use `devspaces --help` to know about updated commands.


### Start Devspaces 

This guide assumes that user is inside `devspaces` folder of the repository.


1.  Create DevSpaces.

```bash
devspaces create
```

2. Start your devspaces.
```bash
devspaces start linguist
```

3. Start containers synchronization.

```bash
cd ../
devspaces bind linguist
```
4. Get some information about container. 

```bash
devspaces info linguist
```

5. Connect to development container. Wait until source code will be synced. You may find out sync status by browsing `http://localhost:49152/` in your web browser.

```bash
devspaces exec linguist
```

6. Prepare environment.

```bash
script/bootstrap
```

7. Download samples.

```bash
bundle exec rake samples
```

8. Run linguist.

```bash
bundle exec bin/github-linguist --breakdown
```

9. You may run the test by the command.

```bash
bundle exec rake test
```

## Running Linguist via Docker-Compose file

### Dockerfile
 Dockefile is created on top of `ubuntu` image.
 
### Requirements
 - The project should be cloned from https://github.com/trilogy-group/linguist
 - Docker version 18.06.0-ce
 - Docker compose version 1.22.0
  
### Quick Start
- Clone the repository
- Open a terminal session to that folder
- Run `docker/docker-cli start`
- Run `docker/docker-cli exec`
- At this point you must be inside the docker container, in the root folder of the project. From there, you can run the commands as usual:
	- `script/bootstrap` to prepare the environment
	- `bundle exec rake samples` to download samples
	- `bundle exec bin/github-linguist --breakdown` to run linguist
	- `bundle exec rake test` to run tests.
	
- When you finish working with the container, type `exit`
- Run `docker/docker-cli stop` to stop and remove the service.
 
 Please refer to [Contributing](../CONTRIBUTING.md) doc for more details on the building and running the app.
