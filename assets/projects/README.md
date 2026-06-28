# Tasarım görselleri — 3 adımda ekleme

Fotoğraflar artık tarayıcıya değil, **repo içinde dosya** olarak durur. Böylece tek tasarıma
10–20 görsel koysan bile site hızlı kalır. Senin tek işin: **dosyaları doğru isimle doğru klasöre yüklemek.**

## Adım 1 — Klasörü hazırla

Her tasarımın bir **slug**'ı var (paylaşım linki adı, örn. `kalip-no1`). O slug ile bir klasör aç:

```
assets/projects/kalip-no1/
```

İçine fotoğrafları **şu sabit isimlerle** koy:

```
assets/projects/kalip-no1/cover.webp     ← KAPAK (3B duvarda + detay hero'da görünen)
assets/projects/kalip-no1/01.webp
assets/projects/kalip-no1/02.webp
assets/projects/kalip-no1/03.webp
...
assets/projects/kalip-no1/10.webp
```

- Format **.webp** önerilir (en küçük boyut). `.jpg` / `.png` de olur — panelde aynı formatı seç.
- İsimler tam böyle olmalı: `cover`, `01`, `02`… (iki haneli, boşluk/Türkçe karakter yok).
- Önerilen: uzun kenar ~1600–2000px, dosya başına < 500 KB. (webp'e çevir: https://squoosh.app)
- Dikey/yatay fark etmez — site kırpmadan, oranını koruyarak gösterir.

## Adım 2 — Panelde otomatik yol oluştur

Siteyi `?duzenle=mert2026` ile aç → ✎ → ilgili tasarımda:

1. **Paylaşım linki adı (slug):** `kalip-no1`
2. **⚡ HIZLI KURULUM** kutusunda: **adet** (örn. 10) + **format** (webp) seç → **"Yolları oluştur"**.

Sistem şunları otomatik yazar (tek tek uğraşmazsın):
`cover.webp` (kapak) + `01.webp … 10.webp` (galeri).

> İstersen yine elle **+ Görsel** ile tek tek path ekleyebilir, **+ Bölüm Başlığı** ile araya
> "Look photos / Detail shots / Process" gibi başlık koyabilir, her görsele TR/EN açıklama ve
> "Tam genişlik" seçeneği verebilirsin.

## Adım 3 — Yükle & yayınla

Dosyaları `assets/projects/<slug>/` klasörüne (GitHub'a sürükle-bırak ile) yükle ve commit et.
GitHub Pages 1–2 dakikada günceller. Path doğruysa görseller otomatik görünür.

- Bir dosya eksikse/yanlışsa site **kırık görsel göstermez**, şık bir "Görsel bulunamadı"
  placeholder'ı gösterir; panelde de o görselin önizlemesi uyarı verir.
- Tam URL de yazabilirsin (`https://...` Drive/Behance/CDN). Karışık kullanılabilir.

## Örnek: 10 fotoğraflı bir tasarım

```
assets/projects/kalip-no1/
├── cover.webp     (kapak)
├── 01.webp
├── 02.webp
├── 03.webp
├── 04.webp
├── 05.webp
├── 06.webp
├── 07.webp
├── 08.webp
├── 09.webp
└── 10.webp
```

Panelde: slug = `kalip-no1`, adet = `10`, format = `webp` → "Yolları oluştur". Bitti.
