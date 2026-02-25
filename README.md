## Personal testing fork
This fork is currently maintained for personal testing only.

It integrates these patch sets:
- `klizas/aur`
- `craigds/fix-vhci-port-change-notification` (including merged `AdityaGarg8` updates)
- `clanoftheducks/clanoftheducks-aaudio-patch1`

Current status on my system: S3 suspend/resume appears to work (almost) reliably for me. I got a "desync" error once in ~40 suspend/resume cycles.

Test system:
- Host: MacBook Pro 16,2 A2251 (13-inch, 2020, Four Thunderbolt 3 ports)
- OS: Fedora Linux 43 (Workstation Edition), x86_64
- Kernel: `6.18.12-210.t2.fc43.x86_64`
- CPU/GPU: Intel Core i5-1038NG7 / Intel Iris Plus Graphics G7
- Kernel cmdline: `intel_iommu=on iommu=pt pcie_ports=native mem_sleep_default=deep`

# MacBook Bridge/T2 Linux Driver
A driver for MacBook models 2018 and newer, implementing the VHCI (required for mouse/keyboard/etc.) and audio functionality.

The project is divided into 3 main components:
- BCE (Buffer Copy Engine) - this is what the files in the root directory are for. This estabilishes a basic communication channel with the T2. VHCI and Audio both require this component.
- VHCI - this is a virtual USB host controller; keyboard, mouse and other system components are provided by this component (other drivers use this host controller to provide more functionality, however USB drivers are not in this project's scope).
- Audio - a driver for the T2 audio interface, currently only audio output is supported.

Please note that the `master` branch does not currently support system suspend and resume.

If you want to support me, you can do so by donating to me on PayPal: https://paypal.me/mcmrarm




