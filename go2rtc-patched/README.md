# go2rtc (patched)

Upstream go2rtc 1.9.15 treats the whole 172.16.0.0/12 range as Docker networks
and skips it for HomeKit mDNS and WebRTC host candidates. When the LAN itself
uses this range (ex. 172.16.200.0/24), HomeKit fails with
`no interfaces for listen`.

This build adds `GO2RTC_DOCKER_NETS` (set in `config.yaml`) so only the HAOS
internal bridges (`172.30.32.0/23`, `172.30.232.0/23`) are skipped.

Source: https://github.com/luiseok/go2rtc

Uses the same `/config/go2rtc.yaml` as the official go2rtc app.
Stop/uninstall the official go2rtc app first (ports 1984/8554/8555 conflict).
