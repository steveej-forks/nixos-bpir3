# NixOS on BPi-R3

This respository contains community supported patches that are necessary to run NixOS on BananaPi-R3 and use it as a fully fledged router.

## Getting started

Build an SD-Image with:

```sh
$ nix build -L '.#nixosConfigurations.bpir3.config.system.build.sdImage'
```

## Features

| feature                   | kernel                                                | nixos                                                                                       |
| ------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| dual radios               | ✔️                                                    | ✔️ (via hostapd)                                                                            |
| Hardware acceleration     | ✔️                                                    | ✔️ ([flow offloading](https://www.kernel.org/doc/html/latest/networking/nf_flowtable.html)) |
| Wireless Event Dispatcher | https://github.com/steveej-forks/nixos-bpir3/issues/2 | ?                                                                                           |

## Known issues

1. [wifi doesn't work when using uart adapter](https://github.com/openwrt/mt76/issues/702)
2. [some devices report incorrect temperature for 2.4 GHz chip](https://github.com/openwrt/mt76/issues/729)

## Real configs

- https://github.com/ghostbuster91/nixos-router
  (bridge eth ports, hw offload, dnsmasq, prometheus, promtail, sops)

## Resources

- [Official forum](https://forum.banana-pi.org/c/banana-pi-bpi-r3/62)
- [NixOS based router Part 1](https://github.com/ghostbuster91/blogposts/blob/main/router2023/main.md)
- [NixOS based router Part 2](https://github.com/ghostbuster91/blogposts/blob/main/router2023-part2/main.md)
