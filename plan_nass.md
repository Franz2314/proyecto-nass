# Proyecto NAS — Planificación

## Hardware sugerido
- **HDD**: 4 × 10 TB (RAID 5/6)
- **SSD**: 2 × 4 TB (caché o apps)
- **RAM**: con ECC si los datos importan
- **UPS**: inversor con apagado graceful
- **Consumo**: ~60-90W 24/7 (~$10-15/mes luz)

## RAID
| Tipo | Útil | Seguridad |
|------|------|-----------|
| RAID 5 | ~30 TB | 1 disco falla |
| RAID 6 | ~20 TB | 2 discos fallan |
| RAID 10 | ~20 TB | mirror, más rápido |

## Sistema
- **SO**: Linux (Debian/Ubuntu Server minimal, sin GUI)
- **Sistema de archivos**: ZFS (OpenZFS) o Btrfs (checksums, snapshots, compresión, bit rot protection)
- **Ext4 no protege de corrupción silenciosa**

## Software (todo en Docker)
- **Cloud**: Nextcloud (Google Drive self-hosted)
- **Media server**: Jellyfin (Netflix self-hosted, apps para TV/celular)
- **Automación**: Radarr, Sonarr, *arr suite
- **VPN acceso remoto**: Tailscale (recomendado) o WireGuard

## Acceso remoto
- **Wake-on-LAN**: encender el NAS solo cuando se necesite (viajes, backups)
- **VPN**: Tailscale/WireGuard — no exponer puertos directamente a internet
- **DDNS**: solo si no se usa VPN

## Backup
- RAID NO es backup (protege contra fallo de disco, no contra borrado/incendio/robo)
- Backup offsite obligatorio (otro NAS, cloud cifrado, disco externo rotativo)

## Energía
- Spindown de discos en inactividad
- Wake-on-LAN para uso bajo demanda
- Apagado completo cuando no se viaje ni se necesite
