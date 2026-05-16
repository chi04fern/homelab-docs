# Hardware

## Ninkear M6 — Main Server

| Component | Details |
|---|---|
| **CPU** | AMD Ryzen 5 6600H |
| **GPU** | AMD Radeon 680M (integrated) |
| **RAM** | ~16 GB |
| **Disk** | ~171 GB |
| **OS** | Ubuntu 24.04 LTS |
| **Typical uptime** | 7+ days continuous |

The integrated Radeon 680M GPU is used for **hardware acceleration** in Jellyfin via VA-API, avoiding software transcoding that would heavily tax the CPU.

## Acer Nitro 5 — Main Workstation

| Component | Details |
|---|---|
| **CPU** | AMD Ryzen 9 6900HX |
| **GPU** | NVIDIA RTX 3070 Ti |
| **RAM** | 32 GB |
| **Role** | Gaming, development, daily driver |

Also used for development and connecting to homelab services via WireGuard or LAN.
