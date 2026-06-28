# Tasarım görselleri — buraya nasıl ekleyeceğin

Bu klasör, müzedeki her tasarımın fotoğraflarını tutar. Fotoğraflar artık tarayıcıya
(base64 olarak) değil, **repo içinde dosya** olarak durur. Böylece tek tasarıma 10–20 görsel
koysan bile site hızlı ve hafif kalır.

## 1) Klasör ve isimlendirme

Her tasarım için kendi slug'ı (paylaşım linki adı) ile bir klasör aç:

```
assets/projects/<slug>/cover.webp      ← kapak (3B duvarda + hero'da görünen)
assets/projects/<slug>/01.webp
assets/projects/<slug>/02.webp
assets/projects/<slug>/03.webp
...
```

Örnek (slug = `kalip-no1`):

```
assets/projects/kalip-no1/cover.webp
assets/projects/kalip-no1/01.webp
assets/projects/kalip-no1/02.webp
```

- Format: **.webp** önerilir (en küçük boyut). `.jpg` / `.png` de olur.
- İsimler basit ve sıralı olsun: `01`, `02`, `03`… (boşluk/türkçe karakter kullanma).
- Önerilen genişlik: uzun kenar **~1600–2000px**, dosya başına **< 500 KB**.
  (webp'e çevirmek için: https://squoosh.app — sürükle, bırak, indir.)

## 2) Edit panelinde path'i yazma

Siteyi `?duzenle=mert2026` ile aç → ✎ → ilgili tasarımda:

- **Paylaşım linki adı (slug):** `kalip-no1`
- **Kapak görseli:** `assets/projects/kalip-no1/cover.webp`
- **Galeri → + Görsel** ile her satıra path yaz:
  - `assets/projects/kalip-no1/01.webp`
  - `assets/projects/kalip-no1/02.webp`
  - …
- İstersen **+ Bölüm Başlığı** ile araya "Look photos / Detail shots / Process" gibi ara başlık ekle.
- Her görselde **açıklama (TR/EN)** ve **Tam genişlik** seçeneği var (kapalıyken 2 kolon grid).

Tam URL de yazabilirsin: `https://...` (Drive/Behance/CDN). Karışık kullanabilirsin.

## 3) Yayına alma

Görselleri bu klasöre koyup GitHub'a yükledikten sonra path'leri panele yaz ve
panelin altından **İNDİR** ile yeni `index.html`'i alıp repoya koy (ya da panel değişikliklerini
commit et). GitHub Pages 1–2 dakikada günceller.

> Not: Edit paneli artık fotoğrafı tarayıcıya gömmez; yalnızca **path/URL + sıralama + metinler**
> kaydedilir. Bu yüzden görsel dosyalarının repoda bulunması gerekir.
