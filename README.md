# Home Lab

My home lab — spare parts, old hardware, and stubbornness. Glendale, AZ.

> **Note on addresses:** this repo uses example IPv6 addresses only
> (ULA range). Nothing here reflects the real addressing of my network.

## The stack

- **Umbrel server** — the always-on box. Pi-hole for network-wide ad
  blocking, Immich for photo backup, Plex + Threadfin for OTA live TV,
  Home Assistant for the smart home.
- **Hades Canyon NUC** (Windows 11 Pro) — download box behind VPN,
  Plex server, and local AI (Ollama + Open WebUI).
- **Dell laptop** — daily driver, on the tailnet.
- **Tailscale** — ties it all together; everything's reachable from anywhere.

## Example IPv6 layout

How a lab like this can be laid out on IPv6 using a ULA prefix.
(Example addresses — not real.)

```
fd42:4242:4242::/48          ULA prefix (example)

fd42:4242:4242::1            router / gateway
fd42:4242:4242::10           hypervisor / main server
fd42:4242:4242::20           NAS / bulk storage
fd42:4242:4242::30           Pi-hole (DNS + DHCP)
fd42:4242:4242::40           Plex + media stack
fd42:4242:4242::50           Home Assistant
fd42:4242:4242::60           Ollama / local AI box
fd42:4242:4242:1::/64        trusted LAN
fd42:4242:4242:2::/64        IoT / smart-home gear
fd42:4242:4242:3::/64        guest network
```

Why ULA: globally unique locally, never collides with a VPN or a
friend's LAN, and keeps working if the ISP renumbers your prefix.
Put IoT on its own /64 and firewall it off from the trusted LAN.

## Notes

- Storage: a big USB drive on the server holds media, photo backups,
  and archives.
- Backups: the important stuff gets backed up. The rest is a learning
  experience.
- Power: the whole lab sips power — the AI box costs a few bucks
  a month to run.

## Scripts

Small utilities I've written along the way live here as I clean them up
for sharing. Nothing fancy — just things that solved a real problem once.
