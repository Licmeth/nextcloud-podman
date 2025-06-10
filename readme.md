# Nextcloud for Podman
The un-official Nextcloud for rootless Podman based on the Nextcloud AIO repo.

Included are:
- Nextcloud
- High performance backend for Nextcloud Files
- Nextcloud Office (optional)
- High performance backend for Nextcloud Talk and TURN-server (optional)
- Nextcloud Talk Recording-server (optional)
- Backup solution (optional, based on [BorgBackup](https://github.com/borgbackup/borg#what-is-borgbackup))
- Imaginary (optional, for previews of heic, heif, illustrator, pdf, svg, tiff and webp)
- ClamAV (optional, Antivirus backend for Nextcloud)
- Fulltextsearch (optional)
- Whiteboard (optional)
- Docker Socket Proxy (optional, needed for [Nextcloud App API](https://github.com/cloud-py-api/app_api#nextcloud-appapi))
- [Community containers](https://github.com/nextcloud/all-in-one/tree/main/community-containers#community-containers)
<details><summary>And much more:</summary>

- Simple web interface included that enables easy installation and maintenance
- [Easy updates included](https://github.com/nextcloud/all-in-one#how-to-update-the-containers)
- Update and backup notifications included
- Daily backups can be enabled from the AIO interface which also allows updating all containers, Nextcloud and its apps afterwards automatically
- Instance restore from backup archive via the AIO interface included (you only need the archive and the password in order to restore the whole instance on a new AIO instance)
- APCu as local cache
- Redis as distributed cache and for file locking
- Postgresql as database
- PHP-FPM with performance-optimized config (e.g. Opcache and JIT enabled by default)
- A+ security in Nextcloud security scan
- Ready to be used behind existing [Reverse proxies](https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md)
- Can be used behind [Cloudflare Tunnel](https://github.com/nextcloud/all-in-one#how-to-run-nextcloud-behind-a-cloudflare-tunnel)
- Can be used via [Tailscale](https://github.com/nextcloud/all-in-one/discussions/5439)
- Ready for big file uploads up to 10 GB on public links, [adjustable](https://github.com/nextcloud/all-in-one#how-to-adjust-the-upload-limit-for-nextcloud) (logged in users can upload much bigger files using the webinterface or the mobile/desktop clients since chunking is used in that case)
- PHP and web server timeouts set to 3600s, [adjustable](https://github.com/nextcloud/all-in-one#how-to-adjust-the-max-execution-time-for-nextcloud) (important for big file uploads)
- Defaults to a max of 512 MB RAM per PHP process, [adjustable](https://github.com/nextcloud/all-in-one#how-to-adjust-the-php-memory-limit-for-nextcloud)
- Automatic TLS included (by using Let's Encrypt)
- Brotli compression enabled by default for javascript, css and svg files which reduces Nextcloud load times
- HTTP/2 and HTTP/3 enabled
- "Pretty URLs" for Nextcloud are enabled by default (removes the index.php from all links)
- Video previews work out of the box and when Imaginary is enabled, many recent image formats as well!
- Only one domain and not multiple domains are required for everything to work (usually you would need to have one domain for each service which is much more complex)
- [Adjustable location](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) of Nextcloud's datadir (e.g. good for easy file-sharing with host system on Windows and MacOS)
- By default confined (good for security) but can [allow access to additional storages](https://github.com/nextcloud/all-in-one#how-to-allow-the-nextcloud-container-to-access-directories-on-the-host) in order to enable the usage of the local external storage feature
- Possibility included to [adjust default installed Nextcloud apps](https://github.com/nextcloud/all-in-one#how-to-change-the-nextcloud-apps-that-are-installed-on-the-first-startup)
- Nextcloud installation is not read only - that means you can apply patches if you should need them (instead of having to wait for the next release for them getting applied)
- `ffmpeg`, `smbclient`, `libreoffice` and `nodejs` are included by default
- Possibility included to [permanently add additional OS packages into the Nextcloud container](https://github.com/nextcloud/all-in-one#how-to-change-the-nextcloud-apps-that-are-installed-on-the-first-startup) without having to build your own Docker image
- Possibility included to [permanently add additional PHP extensions into the Nextcloud container](https://github.com/nextcloud/all-in-one#how-to-add-php-extensions-permanently-to-the-nextcloud-container) without having to build your own Docker image
- Possibility included to [pass the needed device for hardware transcoding](https://github.com/nextcloud/all-in-one#how-to-enable-hardware-acceleration-for-nextcloud) to the Nextcloud container
- Possibility included to [store all docker related files on a separate drive](https://github.com/nextcloud/all-in-one#how-to-store-the-filesinstallation-on-a-separate-drive)
- [LDAP can be used as user backend for Nextcloud](https://github.com/nextcloud/all-in-one/tree/main#ldap)
- Migration from any former Nextcloud installation to AIO is possible. See [this documentation](https://github.com/nextcloud/all-in-one/blob/main/migration.md)
- [Fail2Ban can be added](https://github.com/nextcloud/all-in-one#fail2ban)
- [phpMyAdmin, Adminer or pgAdmin can be added](https://github.com/nextcloud/all-in-one#phpmyadmin-adminer-or-pgadmin)
- [Mail server can be added](https://github.com/nextcloud/all-in-one#mail-server)
- Nextcloud can be [accessed locally via the domain](https://github.com/nextcloud/all-in-one#how-can-i-access-nextcloud-locally)
- Can [be installed locally](https://github.com/nextcloud/all-in-one/blob/main/local-instance.md) (if you don't want or cannot make the instance publicly reachable)
- [IPv6-ready](https://github.com/nextcloud/all-in-one/blob/main/docker-ipv6-support.md)
- Can be used with [Docker rootless](https://github.com/nextcloud/all-in-one/blob/main/docker-rootless.md) (good for additional security)
- Runs on all platforms Docker supports (e.g. also on Windows and Macos)
- Included containers easy to debug by having the possibility to check their logs directly from the AIO interface
- [Docker-compose ready](./compose.yaml)
- Can be installed [without a container having access to the docker socket](https://github.com/nextcloud/all-in-one/tree/main/manual-install)
- Can be installed with [Docker Swarm](https://github.com/nextcloud/all-in-one#can-i-run-this-with-docker-swarm)
- Can be installed with [Kubernetes](https://github.com/nextcloud/all-in-one/tree/main/nextcloud-aio-helm-chart)
- Almost all included containers Alpine Linux based (good for security and size)
- Many of the included containers run as non-root user (good for security)
- Many of the included containers have a read-only root-FS (good for security)
- Included containers run in its own docker network (good for security) and only really necessary ports are exposed on the host
- [Multiple instances on one server](https://github.com/nextcloud/all-in-one/blob/main/multiple-instances.md) are doable without having to deal with VMs
- Adjustable backup path or remote borg repository from the AIO interface (good to put the backups e.g. on a different drive if using a local backup path)
- Possibility included to also back up external Docker Volumes or Host paths (can be used for host backups)
- Borg backup can be completely managed from the AIO interface, including backup creation, backup restore, backup integrity check and integrity-repair
- Other forms of [remote backup](https://github.com/nextcloud/all-in-one#are-remote-borg-backups-supported) are indirectly possible
- Updates and backups can be [run from an external script](https://github.com/nextcloud/all-in-one#how-to-stopstartupdate-containers-or-trigger-the-daily-backup-from-a-script-externally). See [this documentation](https://github.com/nextcloud/all-in-one#how-to-enable-automatic-updates-without-creating-a-backup-beforehand) for a complete example.

</details>
