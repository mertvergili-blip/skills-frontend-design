# Öğrenilen Skill'ler — Frontend & Tasarım Özeti

> skills.sh kataloğundan bu repo (statik editoryal HTML sitesi) için en faydalı **11 skill** kurulup
> derinlemesine öğrenildi. Kurulu dosyalar: `.agents/skills/<skill>/SKILL.md`.
> Tam 600 skill'lik katalog için bkz. [`SKILLS-CATALOG.md`](./SKILLS-CATALOG.md).

## Kurulan skill'ler

| Skill | Kaynak | Ne işe yarar |
|-------|--------|--------------|
| `frontend-design` | anthropics/skills ★ | Şablon gibi durmayan, özgün görsel yön; palet/tipografi/layout kararları |
| `web-design-guidelines` | vercel-labs/agent-skills ★ | UI kodunu Web Interface Guidelines'a göre denetler (canlı kuralları WebFetch ile çeker) |
| `high-end-visual-design` | leonxlnx/taste-skill | "Awwwards" seviyesi ajans estetiği; ucuz görünen AI default'larını yasaklar |
| `minimalist-ui` | leonxlnx/taste-skill | Sıcak monokrom, editoryal, bento-grid, düz/flat minimalizm |
| `emil-design-eng` | emilkowalski/skills | Animasyon/etkileşim mühendisliği; easing, süre, spring, mikro-detaylar |
| `brand-guidelines` | anthropics/skills ★ | Anthropic marka renk/tipografi standartları |
| `canvas-design` | anthropics/skills ★ | Poster/sanat (.png/.pdf) için görsel tasarım felsefesi üretimi |
| `web-artifacts-builder` | anthropics/skills ★ | React+Tailwind+shadcn ile karmaşık tek-dosya HTML artifact üretimi |
| `webapp-testing` | anthropics/skills ★ | Playwright ile yerel web app test/screenshot/log |
| `accessibility` | addyosmani/web-quality-skills | WCAG 2.2 erişilebilirlik denetimi (POUR, kontrast, klavye, ARIA) |
| `seo` | addyosmani/web-quality-skills | Teknik + sayfa-içi SEO, meta etiketler, JSON-LD yapısal veri |

---

## Çekirdek ilkeler (hepsinin ortak dersi)

**AI default'larından kaçın.** Tüm tasarım skill'leri aynı tuzaklara işaret ediyor:
- Yasak fontlar: **Inter, Roboto, Open Sans, Arial, Helvetica**. Bunun yerine Geist, Clash Display,
  PP Editorial New, Instrument Serif, Newsreader, Plus Jakarta Sans gibi karakterli fontlar.
- Yasak görünümler: mor gradyanlar, her yeri saran `rounded-full`, sert `shadow-md/lg` gölgeler,
  generic 1px gri border, simetrik sıkışık Bootstrap grid, ortalanmış her şey.
- Üç klişe AI paleti: (1) krem `#F4F1EA` + serif + terracotta, (2) siyaha yakın + tek asit yeşili/vermilion,
  (3) hairline çizgili broadsheet. Brief açıkça istemedikçe kullanma.

**Tipografi kişiliği taşır.** Display + body fontunu kasıtlı eşleştir, net tip ölçeği kur, sıkı tracking
(`-0.02em`…`-0.04em`) ve sıkı line-height (`1.1`) başlıklarda. Gövde metni asla saf siyah değil (`#111`).

**Tek imza öğesi.** Cesareti tek yere harca: sayfanın hatırlanacağı tek öğe öne çıksın, gerisi sessiz dursun.

**Makro boşluk + ritim.** Bölümler arası `py-24`…`py-40`. İçeriği `max-w-4xl/5xl` ile sınırla.

---

## Animasyon (emil-design-eng — en teknik ders)

- **Önce "animasyon olmalı mı?" diye sor.** Günde 100+ görülen şey (klavye kısayolu, komut paleti)
  asla animasyon almaz. Modal/drawer/toast standart; nadir/ilk-kez olanlar "delight" alabilir.
- **Easing:** giriş/çıkış → `ease-out`; ekranda hareket/morph → `ease-in-out`; hover/renk → `ease`;
  sabit hareket → `linear`. **UI'da asla `ease-in` kullanma** (yavaş hissettirir).
  Özel eğri: `cubic-bezier(0.23, 1, 0.32, 1)`. iOS drawer: `cubic-bezier(0.32, 0.72, 0, 1)`.
- **Süre:** buton basışı 100-160ms, tooltip 125-200ms, dropdown 150-250ms, modal/drawer 200-500ms.
  **UI animasyonları <300ms.**
- **`scale(0)`'dan başlatma** → `scale(0.95)` + `opacity:0`. Gerçek dünyada hiçbir şey yoktan belirmez.
- Buton `:active` → `transform: scale(0.97)` (anında geri bildirim).
- Popover'lar trigger'ından açılsın (`transform-origin`), modallar merkezden.
- Sadece `transform` ve `opacity` animasyonla (GPU). `top/left/width/height` animasyonlama.
- `transition: all` yerine tam property belirt. Dinamik UI'da keyframe yerine transition (kesintiye uğrayabilir).
- Stagger gecikmeleri 30-80ms. `prefers-reduced-motion` = daha az hareket, sıfır değil.
- `@starting-style` ile JS'siz giriş animasyonu; `IntersectionObserver` ile scroll reveal (scroll event değil).

---

## Erişilebilirlik (WCAG 2.2 — POUR)

- Her görselde `alt`; dekoratifse `alt=""`. İkon butonlara `aria-label` + `aria-hidden` ikon.
- Kontrast: normal metin **4.5:1**, büyük metin **3:1**, UI bileşen **3:1** (AA).
- `:focus-visible` ile görünür odak (`outline: 2px solid; outline-offset: 2px`); asla `outline:none` bırakma.
- Native eleman tercih et (`<button>`, `<a href>`); div'e `role`+`tabindex`+keydown ancak mecbursan.
- `<html lang="tr">`, tek `<h1>`, mantıklı başlık hiyerarşisi, skip link.
- Yeni 2.2: dokunma hedefi **min 24×24px** (rahat 44×44), focus obscured olmasın (`scroll-margin-top`).
- `@media (prefers-reduced-motion: reduce)` ile hareketi kıs.

---

## SEO (teknik + sayfa-içi)

- `<title>` 50-60 karakter, anahtar kelime başta, marka sonda, her sayfa benzersiz.
- `<meta name="description">` 150-160 karakter, benzersiz, CTA içeren.
- `robots.txt` + `sitemap.xml` (zaten repoda var), self-referencing `<link rel="canonical">`.
- Open Graph + Twitter card etiketleri; **JSON-LD yapısal veri** (Organization, Article, BreadcrumbList).
- Görseller: açıklayıcı dosya adı + `alt` + `width/height` + `loading="lazy"` + WebP/AVIF.
- Tek `<h1>`, açıklayıcı anchor metni ("buraya tıkla" değil), HTTPS, hyphenli küçük-harf URL.

---

## Bu repo (`index.html`) için somut öneriler

Bu site sıcak/editoryal bir kişisel/marka sitesi. En uyumlu yön: **`minimalist-ui` + `frontend-design`**
çizgisi (editoryal serif başlıklar, monokrom + tek spot pastel, flat kartlar), `emil-design-eng`
animasyon disiplini ve `accessibility` + `seo` quality-floor.

Uygulanabilir hızlı kazanımlar:
1. **SEO meta**: `index.html`'e benzersiz `<title>`/`description`, Open Graph + Twitter card, JSON-LD
   `Person`/`Organization` ekle (sitemap/robots zaten var).
2. **Erişilebilirlik**: `<html lang>` doğru mu kontrol; ikon/sosyal butonlara `aria-label`; `:focus-visible`
   stilleri; dokunma hedefleri 24px+; form/iletişim alanlarına label.
3. **Animasyon cilası**: mevcut fade-in'leri `ease-out` + `<300ms` + `scale(0.95)→1`'e çek; butonlara
   `:active{scale(0.97)}`; `prefers-reduced-motion` koru.
4. **Tipografi**: gövde saf siyah yerine `#111`; karakterli bir display fontu (Instrument Serif/Newsreader)
   ile editoryal başlık kontrastı.

> İstenirse `web-design-guidelines` skill'i ile `index.html` üzerinde tam bir denetim (file:line raporu)
> çalıştırılabilir.
