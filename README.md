# srcpkgs
Personal Void Linux packages


## Mullvad VPN
The `mullvadvpn-app` directory contains the template needed to generate a `.xbps` file.

### Some things to note:
- Normally the app is installed to `/opt/Mullvad VPN` (e.g. on other distributions), but **here** it is installed to: `/usr/lib/mullvadvpn-app` to maintain consistency with other packages (e.g. Discord, Spotify).
- You will need to [enable](https://docs.voidlinux.org/config/services/index.html#enabling-services) the `mullvad` service for the app to actually work, i.e.:
```
# ln -s /etc/sv/mullvad/ /var/service/
```
- This has not been tested on ARM but I don't see why it wouldn't work. 🤷

This package uses the [official .deb package](https://github.com/mullvad/mullvadvpn-app/releases/tag/2026.1) to avoid building from source. According to a Mullvad developer, the `mullvad-daemon` will soon [transition from the Wireguard Go implementation to GotaTun](https://github.com/void-linux/void-packages/pull/56005#issuecomment-4096788731). Aaand someone has already submitted [a merge request](https://github.com/void-linux/void-packages/pull/56005) to indepenently package said daemon. After the transition is complete and assuming that package is approved, I will consider writing a source-based package for Mullvad's app that depends on that package.