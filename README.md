# Setup script for Redash with Podman on RHEL 8

This is adapted from the Ubuntu 18.04 docker install script here - https://github.com/getredash/setup

This changes out docker for podman and docker-compose for podman-compose the `RHEL 8 Podman Steps` document contains the details of the steps inc where to run the script `setup.sh`

This is the same setup redash use for our official images (for AWS & Google Cloud) and can be used as reference if you want to manually setup Redash in a different environment (different OS or different deployment location).

* `setup.sh` is the script that installs everything and creates the directories.
* `RHEL 8 Podman Steps` is the steps required before running the script (temp before added to script)
* `docker-compose.yml` is the Docker Compose setup we use.
* `packer.json` is Packer configuration we use to create the Cloud images.

## FAQ

### Can I use this in production?

For small scale deployments -- yes. But for larger deployments we recommend at least splitting the database (and probably Redis) into its own server (preferably a managed service like RDS) and setting up at least 2 servers for Redash for redundancy. You will also need to tweak the number of workers based on your usage patterns.

### How do I upgrade to newer versions of Redash?

See [Upgrade Guide](https://redash.io/help/open-source/admin-guide/how-to-upgrade).

### How do I use `setup.sh` on a different operating system?

You will need to update the `install_docker` function and maybe other functions as well.
