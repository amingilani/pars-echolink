# PARS EchoLink

![BalenaCloud Push](https://github.com/amingilani/pars-echolink/workflows/BalenaCloud%20Push/badge.svg)

This EchoLink Node Configuration is based on the [article](http://www.pakhams.com/index.php?option=com_content&view=article&id=178:pi3echolink&catid=45:misc&Itemid=158) by AP2CJ.

Before running, ensure you have [Docker](https://docs.docker.com/get-docker/) installed. This build is meant to be deployed to a balenaOS host, and depends on a host with `ALSA`.

Required variables:

- `ECHOLINK_CALL`: Echolink callsign
- `ECHOLINK_PASS`: Echolink password
- `AUTH_KEY`: The auth key for the device

Optional variables:

- `ENV`: Set this to `dev` to trigger the station to call out its ID every 45 seconds
- `TIMEZONE`: Set this to your local time. The default is `PKT`, but you may want `UTC`
- `PAPERTRAIL_HOST`: Send logs to Papertrail for easier debugging.
- `PAPERTRAIL_PORT`: Send logs to Papertrail for easier debugging.


Helpful commands:

+ `aplay -l`: to list available sound devices
+ `dmesg | awk '/tty/ && /USB/ {print "/dev/"$10}'|tail -1`: shows the USB device serial cable plugged in


## Testing

Note that during testing you cannot run Balena Cloud environment variables. Pass them through docker compose or your Dockerfile.

Prelude:

+ Ensure you have a local development version of balena running
+ Ensure the local host has a USB sound card attached

To test, push to the host with:

```
balena push $balena_dev_device
```


TODO:

+ Fix environment variables in intermediate container
+ deploy via balena cloud
+ Finish dev
+ Expose public ports
