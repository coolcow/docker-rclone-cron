# ghcr.io/coolcow/rclone-cron

This image extends [ghcr.io/coolcow/rclone](https://github.com/coolcow/docker-rclone) with cron support for scheduled sync jobs.

---

## About

For a full description, features, configuration options, and usage examples for Rclone, see the [docker-rclone README](https://github.com/coolcow/docker-rclone#readme).

This image only adds cron support for running scheduled sync jobs inside the container.

---

## Usage

Mount your rclone config and crontab file, then set the `CROND_CRONTAB` environment variable:

```sh
docker run --rm \
  -e PUID=$(id -u) \
  -e PGID=$(id -g) \
  -e CROND_CRONTAB=/crontab \
  -v /path/to/rclone.conf:/home/.rclone.conf:ro \
  -v /path/to/data:/data \
  -v /path/to/logs:/logs \
  -v /path/to/crontab:/crontab:ro \
  ghcr.io/coolcow/rclone-cron
```

Example crontab entry (in `/path/to/crontab`):

```
0 */2 * * * flock -n ~/rclone.lock rclone sync --log-file /logs/rclone.$(date +\%Y\%m\%d_\%H\%M\%S).log /data cloudstorage:
```

---

## Environment Variables

See [docker-rclone Environment Variables](https://github.com/coolcow/docker-rclone#environment-variables) for all options. This image adds:

| Variable         | Default   | Description                           |
|------------------|-----------|---------------------------------------|
| `CROND_CRONTAB`  | /crontab  | Path to crontab file in the container |

---

## License

GPL-3.0. See [LICENSE.txt](LICENSE.txt) for details.
