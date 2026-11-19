# Vize sitesini slayt + sorulardan yeniden kur, yalnız BUders videolarıyla

## Hedef
mat202vize sitesi slaytlar ve taranmış sorulardan eksiksiz yeniden kurulur; videolar yalnız buders.com'da listelenen BUders videoları; BUders videosu olmayan konular en sondaki tek sayfada ayrı ayrı anlatılır.

## Tanım: bitti
- K1-K39'un ve 17 sorunun (A1-A6, B7-B11, C1-C6) her biri sitede var.
- Sitedeki her YouTube ID oEmbed ile BUders ve buders.com'da bir sayfada listeli.
- BUders videosu olmayan konular haftaların arasında değil, yalnız son sayfada; her biri kendi başlığıyla tam anlatım.
- Push edildi, canlı sayfa curl ile kontrol edildi.

## Kararlar
- Kapsam: yalnız mat202vize (Dioganos/mat202vize) — sebep: kullanıcı "slayt ve sorulara bak siteyi yeniden oluştur" dedi; bu site slayt+sorudan kurulu. Eski mat202 video takip sitesi kapsam dışı, raporda söylenir.
- Push işin parçası — sebep: memory canli-site-push; 2026-11-19 kullanıcı açıkça "bitince canlı siteyi güncelle ordan bakıcam" dedi.
- Son sayfada video yok, yalnız yazılı anlatım + ilgili soru — sebep: "alternatif video bulma".
- KISMİ kapsanan konu: videonun öğrettiği çekirdek kısım haftada kalır; videonun hiç değinmediği alt konu son sayfaya gider — sebep: "olmayan konular ... aralara ekleme".
- Videolar yalnız buders.com sayfasında listelenenler; yalnız YouTube kanalında olan sayılmaz — sebep: kullanıcı "buders internet sitesinden" dedi.
- Son sayfaya giden birim konu (K), alt konu değil: yalnız hiç BUders videosu olmayan 7 K. KISMİ konular haftada kalır, notları tam, başta "BUders videolarının başlığında geçmeyen kısım" satırı — sebep: KISMİ'lerin çoğu "doğrulanmadı" (video izlenmedi), alt konuları koparmak çalışma akışını bozar. Yukarıdaki "KISMİ alt konu son sayfaya" kararının yerine geçer.
- "Vize ve Finalde Çıkabilecek Sorular" 17 BUders videosu gömülmez, rehberde link + dürüst not — sebep: konuları belirsiz, BUders sınav örnekleri kök bulma ağırlıklı.
- Formül kâğıdı, slayt hataları, son gün listesi "Sınav hazırlığı" grubunda, son sayfadan önce — sebep: konu değil; son sayfa yalnız videosuz konular.

## Kısıtlar
- Kaynak notlar: `C:\Users\emirc\Downloads\mat202\_notlar\{slaytlar.md, sorular.md, buders.md, site.md}`.
- Eski build: `_notlar/_build2/build.mjs` (2026-11-16) index.html'den eski; sonraki commitler (a4367ed, 90fa87e, c240fa2) doğrudan index.html'e yapıldı.
- Dev server açılmaz; kontrol headless.

## Plan
- F1a BUders tam tarama → `_notlar/buders_v2.md` — açık
- F1b slayt denetimi → `_notlar/slayt_denetim.md` — kapandı: 112/112 sayfa; 45 eksik (E1-E45), 7 yanlış aktarım, 8 yeni slayt hatası (N1 W234 s41 100x→10x, N2 s42 −4h²f″→−2h²f″, N6 W5 s11 3/8 bileşik ×n/3 fazla). slaytlar.md'ye işlenmedi; builder iki dosyayı birlikte okur.
- F1c soru çözüm denetimi → `_notlar/soru_denetim.md` — kapandı: 17/17 metin kâğıtla aynı, son cevaplar doğru (script `_notlar/_soru_tmp/denetim_hesap.py`). DÜZELT: C2, C4 pay satırı 9 ondalıkla. EKSİK 10 alt madde (A2, A3, A4, A4 polinom, A5 e¹ gerekçesi, B7c, B9d, B9f, B10c, C1c), ek metin dosyada hazır. Açık: B11 tablo değeri 0.405 mi 0.4055 mi okunmuyor (cevap 0.8313 / 0.8311).
- F1a kapandı: `_notlar/buders_v2.md` 184 SA videosu + 19 diğer ders, hepsi oEmbed BUders; K: 18 TAM, 14 KISMİ, 7 YOK (K1 K6 K10 K16 K28 K37 K39). 19 videonun süresi yok (HTTP 429). "Vize ve Finalde Çıkabilecek Sorular" 17 video konusu belirlenemedi.
- F2 site yeniden kurulum — açık. Sözleşme: `_notlar/_build3/` parça dosyaları, `@@note|q <id> | <başlık>`, id k01-k39 / a1-c6 / x01.. / rehber formul slhata songun disari; q'larda `<!-- k: -->` etiketi; parçalarda video yok, entegratör koyar.
  - W-A h1+h2 (k02-k15 minus k06,k10) · W-B h3+h4 · W-C h5+son · W-D sorular.html · W-E alistirma.html (ağır) · I build.mjs+videos.json+check.mjs (ilk tur stub, `_out/`)
- F3 push + canlı curl — açık

## Dosya haritası
- `mat202vize/index.html` — tek dosya site (108 KB)
- `_notlar/_build2/` — eski parça dosyaları (w1-w5, q, ek) + build.mjs, KaTeX/mobil kontrol scriptleri

## Ajanlar
- `a90ff56792601933c` — general-purpose, sonnet (orta) — F1a BUders tarama → `_notlar/buders_v2.md`
- `a9e4f52467a3b36b8` — general-purpose, sonnet (orta) — F1b slayt denetimi → `_notlar/slayt_denetim.md`
- `a67b673101749f35a` — general-purpose, opus (ağır) — F1c soru denetimi → `_notlar/soru_denetim.md`
- `a180066204e1baead` — implementer, sonnet — W-A h1.html h2.html kapsam_h12.md
- `a05def0faa263e41e` — implementer, sonnet — W-B h3.html h4.html kapsam_h34.md
- `a11322796c956aec9` — implementer, sonnet — W-C h5.html son.html kapsam_h5son.md
- `a77d9a79b09145bf1` — implementer, sonnet — W-D sorular.html kapsam_sorular.md
- `a6031d80a8ebac2d1` — implementer, opus — W-E alistirma.html kapsam_alistirma.md
- `a9b9b682ad3267502` — implementer, sonnet — I build.mjs videos.json check.mjs (recall for final: real parts → mat202vize/index.html, commit, push)

## Aday
- KaTeX'in `.katex-mathml` kutuları `position:absolute`. Kaydırmalı kapsayıcı (`overflow-x:auto`) `position:relative` değilse tablonun sağındaki bu kutular kırpılmaz ve mobilde sayfa yatay taşar — sebep: `.tw` içindeki formüllü tabloda sw=417 çıktı, `position:relative` ile 0 oldu — kanıt: `_build3\build.mjs` CSS bloku. (ajan I'dan, birebir) — karar bekliyor

## Sürtünme
- Bash hook'u heredoc'u engelledi (dosyaları Write/Edit ile yazdım); node'a `--dump-dom` ile 360 px emülasyonu da güvenilmez çıktı (Edge min pencere genişliği), CDP'ye geçtim. (ajan I)

- KaTeX makinede yok, parça yazarları render kontrolü yapamadı; render kontrolü yalnız I'nın check.mjs (Edge CDN). (W-B)

## W-B sonucu
- h3 7 blok, h4 5 blok; kapsam 56/56 K maddesi, 25/25 denetim satırı, 10/10 §5.
- Yeni slayt bulguları (denetimde yok): W234 s28 hata mertebesi (Δ,∇ O(h), δ O(h²); slayt Δ² O(h²), δ³-δ⁴ O(h⁴) diyor); s46 sınırda FD1/BD1 listeliyor ama s49/s51 "asla FD1/BD1"; s51 adım 4 "h_opt'u geç" → "geçme".
- Slayt alıntılarında "—" virgül/noktaya çevrildi (birebir değil).

## W-A sonucu
- h1 5 blok, h2 7 blok; kapsam 136/136, kontrol.mjs temiz.
- Yeni slayt farkları: G2 s13 ikinci farklar 2 ve 6 (slayt 3, 9); G2 s18 "Beklenen" 6.25 → 4.75; G2 s7 0.877604 aslında 4. derece, P₃(0.5)=0.875; W234 s12-s13 son basamak farkı (s13 doğru); W234 s1-2 "5 çözümlü örnek" ama 5. yok.
- Hocanın slayttaki ders videosu linkleri (G2 s12, s15; BUders değil) konmadı — sebep: yalnız BUders.
- k03 anlamlı basamak sayma kuralı slaytta yok, genel kural "slaytta yok" etiketiyle.

## W-C sonucu
- h5 8 blok, son 7 blok; kapsam 143/143; kontrol.mjs temiz.
- Yeni W5 farkları: Simpson n=2 1.71886/0.00058 (slayt 1.71882/0.00054); n=4 1.71832/3.7e-5 (slayt …/1.3e-5); hata oranı 15.65 (slayt 41); √(1+x³) f(2/3)=1.1386, f(4/3)=1.8359 (slayt 1.1041, 1.6916); Δ_b=1.74e-6; s11 "n=4 Simpson n=100 trapezden iyi" e^x için tutmuyor (k37'de işlendi).
- Quiz eşlemesi buders.md Bölüm B'ye göre: Q1→k30, Q4→k32, Q2→k34, Q3→k33,k38, Q5→k38.
- `python` Microsoft Store kısayolu, çalışmıyor; scriptler node. (sürtünme)

## W-E sonucu
- 23 alıştırma x01-x23; 14 tip + §4.3 + eski 17 ekalis bağlı. Önemliler: x03 hata yayılımı, x04 1−cosθ, x08 Horner, x19 optimal h, x20 h/2 oranı, x22 karma n=7,10, x23 n seçimi.
- Eski ekalis: √x ekstrapolasyon açıklaması yanlıştı (x06'da düzeldi); 3/8 ve karma son basamaklar.
- Revize gönderildi: x14 gerçek hata > kuramsal sınır (3 ondalık veri) → veri ondalığını artır; NİFİF ilk geçişte "(slaytta NIFF)".

## W-D sonucu
- sorular.html: rehber, formul, a1-c6 (17), slhata (H1-H20 + N1-N8 = 28), songun, disari. Kontrol 0 hata.
- soru_denetim 14 madde uygulandı. C2 pay 9 ondalıkla 0.001410680, sonuç 0.705340 (tam 0.705341). B8c "terim arttıkça yaklaşır" yanlıştı (0.878, 1.0613, 0.9748), düzeltildi. C2 hata (h²/4)|f⁽⁵⁾|=0.00177 → O(h²), s28 "δ³ O(h⁴)" yanlış.
- Formül kâğıdına 19 grup eklendi; slaytta olmayan hata terimleri "standart" etiketli.

## I ilk tur sonucu
- Kabuk mevcut index.html'den; korunan: tema, KaTeX CDN, arama `/`, ←/→, fit, `#id+` çözüm açma, nocookie oynatıcı, watch_videos, print CSS.
- İlerleme anahtarı `m202v3` (ID bazlı); eski `m202vize`/`m202d` taşınıyor.
- videos.json: 39 K, 7 boş, 73 tekil ID, yabancı 0; 17 soru eşli. `_test/videos_uret.mjs` üretir.
- Final komut: `node build.mjs <çıktı> && node check.mjs <çıktı> --tam` (`_notlar/_build3/`).
- Stub check: a-g OK. Eski sitedeki 20 buders quiz linki yeni parçalara bağlı (W-A/W-C brieflerinde var).

## Durum
Son tamamlanan: bütün parçalar hazır (W-A..W-E kapandı; x14 revize tamam: 6 ondalık veri, hata sınır altında)
Sıradaki: I final turu (recall) — build + check --tam + ekran görüntüsü + index.html + commit + push + canlı curl

## Açık sorular
