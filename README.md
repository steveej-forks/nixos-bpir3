# NixOS on BPi-R3

This respository contains community supported patches that are necessary to run NixOS on BananaPi-R3 and use it as a fully fledged router.

## Getting started

Build an SD-Image with:

```sh
$ nix build -L '.#nixosConfigurations.bpir3.config.system.build.sdImage'
```

## Features

| feature                   | kernel | nixos                                                                                        |
| ------------------------- | ------ | -------------------------------------------------------------------------------------------- |
| dual radios               | [x]    | [x] (via hostapd)                                                                            |
| Hardware acceleration     | [x]    | [x] ([flow offloading](https://www.kernel.org/doc/html/latest/networking/nf_flowtable.html)) |
| Wireless Event Dispatcher | #2     | ?                                                                                            |

## u-boot

### u-boot patches

Deriving random static MAC addresses for interfaces is done via patches
applied in the custom u-boot of this repository. This can be pulled in as
an input if desired.

```nix
{
  inputs = {
    bpir3.url = "github:nakato/nixos-bpir3-example";
  };

  # And used somewhere
  firmware = bpir3.packages.aarch64-linux.armTrustedFirmwareMT7986;
}
```

## real configs

- https://github.com/ghostbuster91/nixos-router
  (bridge eth ports, hw offload, dnsmasq, prometheus, promtail, sops)
