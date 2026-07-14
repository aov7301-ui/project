# EPG Auto-Update

EPG XMLTV Indonesia yang diperbarui otomatis oleh GitHub Actions setiap 6 jam.

## URL EPG

```
https://github.com/aov7301-ui/project/raw/refs/heads/main/epgs/guide.xml.gz
```

Masukkan URL di atas ke aplikasi/panel IPTV yang mendukung XMLTV (`.xml.gz`).

## Cara kerja

1. Workflow `.github/workflows/epg.yml` berjalan tiap 6 jam (cron) atau manual lewat tab **Actions**.
2. Workflow meng-clone [iptv-org/epg](https://github.com/iptv-org/epg) lalu mengambil jadwal untuk channel yang terdaftar di `epgs/custom.channels.xml`.
3. Hasilnya divalidasi, dikompres menjadi `epgs/guide.xml.gz`, lalu di-commit kembali ke repo ini.

## Menambah / mengurangi channel

Edit `epgs/custom.channels.xml`. Daftar channel yang didukung tiap situs ada di folder
[sites di iptv-org/epg](https://github.com/iptv-org/epg/tree/master/sites) — salin baris
`<channel ...>` dari file `<situs>.channels.xml` yang sesuai.

Setelah file diubah dan di-push, workflow otomatis jalan ulang.
