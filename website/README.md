# TAG App Delivery Website

This directory contains a [Hugo](https://gohugo.io) web site published via [Netlify](https://www.netlify.com/) to <https://tag-app-delivery.cncf.io/>.

When the `main` branch of this repo is updated a fresh build and deploy of the website is executed. Recent Netlify builds and deployments are listed at <https://app.netlify.com/sites/tag-app-delivery>.

## Setting up a dev instance

There a two ways to run the webserver for developing the site.

### Run in Dev Container
With a development container (called workspace), the entire toolchain can be bundled up and run in any environment that can run containers.

Requirements:
- [DevPod](https://devpod.sh/docs/getting-started/install)
- An environment with a [DevPod provider](https://devpod.sh/docs/managing-providers/what-are-providers), e.g. [Docker Desktop](https://www.docker.com/products/docker-desktop/)

DevPod can be run with a GUI or via CLI.

#### GUI

To start a workspace through the GUI click the below button.
Then choose the desired provider and IDE.

[![Open in DevPod!](https://devpod.sh/assets/open-in-devpod.svg)](https://devpod.sh/open)

#### CLI
To startup a devcontainer through the CLI, follow below steps
```
# Add a provider for your environment, e.g. docker (this only needs to be done once)
devpod provider add docker

# Create workspace from local path
git clone git@github.com:cncf/tag-app-delivery.git
cd tag-app-delivery
devpod up .

# OR Create workspace from remote git repository
devpod up github.com/cncf/tag-app-delivery

# Start the workspace
devpod up tag-app-delivery --ide openvscode
```

Once the workspace is up, DevPod will start your IDE. Open up a terminal to execute the server startup script

```
/bin/bash .devcontainer/start-server.sh
```
Navigate to http://localhost:1313 with your browser to view the site.

### Run directly on machine

To set up a local dev environment make sure you have [Hugo Extended](https://gohugo.io/installation/linux/#editions) and [npm](https://www.npmjs.com/) installed, then run the server startup script:

```
/bin/bash .devcontainer/start-server.sh
```
the output will tell you which port the webserver is serving.

## Add content to website
Generally speaking, there are three types of content we feature on the website:
1. **Projects looking for contributions**  
These are strictly scoped in both time and content. People can contribute without the need for committing long-term.
1. **Blogposts**  
Updates about the TAG.
1. **Working Groups**  
Longrunning interest groups, the scope of which might change. A working group can create multiple projects.

### Create new call for contribution
```
cd website
hugo new content contribute/<project title>.md
```

### Create new blogpost
```
cd website
AUTHOR=ll hugo new content blog/<post title>.md
```

### Create new working group
```
cd website
hugo new wgs/<working group name>
```