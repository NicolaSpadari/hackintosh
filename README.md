# Hackintosh (OpenCore, Asus Z390-F, i7 9700K, GTX 1080ti)

![](.//about-this-mac.png)

## Software

- OpenCore: 0.8.8
- OCLP: 0.5.3
- MacOS: 12.6.2 (Monterey)

## Hardware

- Motherboard: Asus Z390-F
  - Note: Bluetooth is handled by an USB adapter
- CPU: Intel Core i7-9700K
- GPU: Nvidia GeForce GTX 1080
- RAM: Corsair 32GB DDR4 Vengeance LPX 3200 MHz
- SSD:
  - Samsung 970 Evo 250GB, M.2
  - Samsung 960 Evo 250GB, M.2
  - Samsung 860 Evo 500GB, 2.5"
  - Samsung 860 Evo 500GB, 2.5"

## `config.plist`

Values that are `{{REPLACE_ME}}` must be replaced with actual values.

### Quirks

#### `DeviceProperties/Add/PciRoot(0x0)/Pci(0x2,0x0)`

- With macOS 10.15.5 the recommended value `07009B3E` for `AAPL,ig-platform-id` isn't working (anymore) for Intel UHD 630 and will result in a black screen.
  - Fix: Use the alternative value `00009B3E`.
- Using only the suggested keys from the [OpenCore Coffee Lake Guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#deviceproperties) `AAPL,ig-platform-id`, `framebuffer-patch-enable` and `framebuffer-stolenmem` aren't sufficient and will result in a black screen after the OpenCore boot sequence.
  - Fix: [iGPU BusID Patching](https://dortania.github.io/OpenCore-Desktop-Guide/extras/gpu-patches.html#igpu-busid-patching) is necessary. After several reboots, it's port 3 and busID `04` to get a video signal (Note: `AAPL,ig-platform-id` must be set to a working value beforehand).

## Bookmarks

- [BIOS Settings](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings)
- [Generate `PlatformInfo` values](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#platforminfo)
- [OpenCore Sanity Checker](https://opencore.slowgeek.com/)
