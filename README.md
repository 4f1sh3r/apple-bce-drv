# MacBook Bridge/T2 Linux Driver
A driver for MacBook models 2018 and newer, implementing the VHCI (required for mouse/keyboard/etc.) and audio functionality.

The project is divided into 3 main components:
- BCE (Buffer Copy Engine) - this is what the files in the root directory are for. This estabilishes a basic communication channel with the T2. VHCI and Audio both require this component.
- VHCI - this is a virtual USB host controller; keyboard, mouse and other system components are provided by this component (other drivers use this host controller to provide more functionality, however USB drivers are not in this project's scope).
- Audio - a driver for the T2 audio interface, currently only audio output is supported.

Please note that the `master` branch does not currently support system suspend and resume.

## Personal testing fork
This fork is currently maintained for personal testing only.

It integrates both patch sets:
- `klizas/aur`
- `craigds/fix-vhci-port-change-notification` (including merged `AdityaGarg8` updates)

Current status on my system: S3 suspend/resume appears to work reliably for me.

Test system:
- Host: MacBook Pro (13-inch, 2020, Four Thunderbolt 3 ports)
- OS: Fedora Linux 43 (Workstation Edition), x86_64
- Kernel: `6.18.12-210.t2.fc43.x86_64`
- CPU/GPU: Intel Core i5-1038NG7 / Intel Iris Plus Graphics G7
- Kernel cmdline: `intel_iommu=on iommu=pt mem_sleep=s2idle pcie_ports=native BOOT_IMAGE=(hd0,gpt3)/vmlinuz-6.18.12-210.t2.fc43.x86_64 root=UUID=ad08bb2e-321b-47c6-a3e0-f3fe428a4c52 ro rootflags=subvol=root mem_sleep_default=deep`

If you want to support me, you can do so by donating to me on PayPal: https://paypal.me/mcmrarm
