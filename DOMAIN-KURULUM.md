# mertvergili.com — domain bağlama (basit rehber)

Domain DNS'i aktifleşince aşağıdaki adımları **sırayla** yap. Şu anki GitHub Pages linkin
(`mertvergili-blip.github.io/skills-frontend-design`) bu işlemler bitene kadar bozulmaz.

> Not: CNAME dosyasını repoya **önceden koymadım** — bilerek. Çünkü domain DNS'i hazır
> olmadan eklenirse github.io adresin geçici olarak erişilemez olabilir. Aşağıdaki sıra güvenli.

## 1) Alan adı sağlayıcında (GoDaddy/Namecheap/İsimtescil vb.) DNS kayıtları ekle

**A) Apex (çıplak) domain — `mertvergili.com`** için 4 adet **A kaydı**:

```
Tip: A   Host: @   Değer: 185.199.108.153
Tip: A   Host: @   Değer: 185.199.109.153
Tip: A   Host: @   Değer: 185.199.110.153
Tip: A   Host: @   Değer: 185.199.111.153
```

(İstersen IPv6 için 4 adet AAAA kaydı da ekleyebilirsin — opsiyonel:
`2606:50c0:8000::153`, `…8001::153`, `…8002::153`, `…8003::153`.)

**B) `www` için 1 adet CNAME:**

```
Tip: CNAME   Host: www   Değer: mertvergili-blip.github.io
```

DNS yayılması 10 dk – birkaç saat sürebilir.

## 2) GitHub Pages'te domaini bağla

1. GitHub'da repoya gir → **Settings → Pages**.
2. **Custom domain** kutusuna `mertvergili.com` yaz → **Save**.
   (Bu adım repoya otomatik bir `CNAME` dosyası ekler — sen elle eklemene gerek yok.)
3. GitHub "DNS check successful" diyene kadar bekle (birkaç dakika).
4. Sertifika hazır olunca **Enforce HTTPS** kutusunu işaretle.

## 3) Sitedeki adresi domaine geçir (paylaşım linkleri + canonical + OG)

1. Siteyi `https://mertvergili.com/?duzenle=mert2026` ile aç → ✎.
2. **SİTE & ANALYTICS → Site adresi** alanına şunu yaz:

   ```
   https://mertvergili.com
   ```

3. Otomatik kaydedilir. Bundan sonra:
   - "Linki kopyala" → `https://mertvergili.com/?design=…` verir,
   - canonical ve Open Graph URL'leri domaine geçer.

> Alternatif (kalıcı/baked): panel altından **İNDİR** ile yeni `index.html` al ve repoya koy —
> böylece `siteKok` değeri dosyaya gömülür.

## 4) Son kontrol

- `https://mertvergili.com` açılıyor mu?
- `https://www.mertvergili.com` da yönleniyor mu?
- Adres çubuğunda kilit (HTTPS) var mı?
- Bir tasarımda "Linki kopyala" → çıkan link `mertvergili.com` ile mi başlıyor?

Takılırsan DNS kayıtlarının ekran görüntüsünü paylaş, birlikte bakarız.
