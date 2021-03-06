# A basic EQDKP docker-compose setup

You'll certainly have to add some backups and such to this. Largely doing a `docker-compose build; docker-compose up` will work providing you've got the `letsencrypt` infra in place. Otherwise you'll need to do that, or run insecure http.

I'm running this on a box with a bunch of vhosts so I needed to have a reverse proxy that didn't require people to go to `https://domain:8443`. You can take a look at the [nginx_reverse_proxy.conf](nginx_reverse_proxy.conf) and wire that up to either another container running nginx, or just work it into your running nginx config.

The [eqdkp.conf](eqdkp.conf) nginx config for the eqdkp php app is largely copy-pasta from the [eqdkp documentation](https://eqdkp-plus.eu/wiki/Nginx#Full_example). Lots of stuff in here is _magic_ and or not really used or well understood (by me); nor does it really need to be imo. I'm certainly not a web server configuration guru, so if people see glaring issues with this I would be happy to accept PRs.

## TODO

- Move the `/opt/eqdkp*` structure to a volume to make it a bit easier to backup.
- Get a script setup with something like `s3cmd` to take backups and move them to S3
- Document/automate the `letsencrypt` portion making it less presumptious