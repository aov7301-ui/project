# 📺 Personal IPTV Project

Koleksi EPG guide, playlist, dan script otomasi untuk keperluan pribadi.
Semua file diperbarui otomatis oleh GitHub Actions.

---

## 🔗 EPG & Playlist

| Jenis | URL |
| --- | --- |
| **EPG (XMLTV .gz)** | https://github.com/aov7301-ui/project/raw/refs/heads/main/epgs/guide.xml.gz |
| **Master Playlist** | https://github.com/aov7301-ui/project/raw/refs/heads/main/IndihomeTV.m3u |

---

## ⚙️ Pipeline Otomatis (GitHub Actions)

| Workflow | Jadwal | Output |
| --- | --- | --- |
| `Update EPG` / `Generate Master EPG Pipeline` | tiap 6 jam | `epgs/guide.xml` + `epgs/guide.xml.gz` + `epgs/channels.txt` |
| `Generate FAST Service Playlists` | tiap 6 jam | `playlists/pluto_all.m3u`, `samsungtvplus_all.m3u`, `roku.m3u`, `tcl.m3u`, `tcl_epg.xml` |
| `Generate Live Events` | tiap 3 jam | `playlists/events.m3u8`, `World_Cup.m3u` (hanya stream yang masih hidup) |
| `Generate RCTI+ Playlists` | tiap 6 jam | `playlists/rctiplus.m3u` + merge ke `IndihomeTV.m3u` |

## 📝 Konfigurasi

- **Daftar channel EPG:** edit `epgs/custom.channels.xml` (format iptv-org, lihat [sites](https://github.com/iptv-org/epg/tree/master/sites)).
- **Channel FAST tambahan untuk EPG:** isi `epgs/extra_ids.txt` (tvg-id PlutoTV/Roku/SamsungTVPlus dari [i.mjh.nz](https://i.mjh.nz/)), atau set secret `M3U_URL`.
- **Filter region/kategori playlist FAST:** edit bagian `CONFIG FILTER & METHOD` di atas `generate_playlists.py`.
- **Sumber live events:** edit list `SOURCES` di `generate_liveevents.py`.

---

## 📡 Sumber

- iptv-org/epg
- matthuisman/i.mjh.nz
- BuddyChewChew
- Vidio, VisionPlus, CubMu, DENS, MaxStream (EPG)
