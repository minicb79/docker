# docker

---

This repo contains my docker layers for creating images that will run applications or devcontainers.

## base

This is the base Dockerfile that will contain the bare minimum config that will be used by all future Dockerfile definitions.

At its heart, it contains a Linux base, git and `.gitconfig` with my git aliases.

It configures the Working directory to be `/app`.

### Building the base

To build base, execute the following:

```bash
docker build -t git-base .
```

### Using the Base Image

You can use this image as a base for your other Dockerfiles:

```Dockerfile
FROM git-base

# Your project-specific instructions
# ...
```

> ## User management
> To add users to any image, add the following snippet, remembering that the higher up in the Dockerfile you place it, to less likely the container will need to be rebuilt.
> 
> ```Dockerfile
> # Create a non-root user
> RUN adduser --disabled-password appuser
> 
> # Copy .gitconfig to the user's home directory
> COPY .gitconfig /home/appuser/.gitconfig
> 
> # Switch to the appuser
> USER appuser
> ```

