# Sayfadaki videoları yalnız BUders kaynaklı yap

## Hedef
`index.html` içindeki tüm videolar ve video linkleri yalnız BUders YouTube kanalı ve buders.com içeriğinden gelsin.

## Tanım: bitti
- Sayfada BUders kanalına ait olmayan tek bir YouTube ID'si kalmaz.
- Her konu için BUders'te karşılık varsa o konur; yoksa video çıkar, buders.com sayfası varsa link kalır.
- Sayfa yapısı, haftalık oynatıcı, "tümünü oynat" linki bozulmaz.

## Kararlar
- BUders'te karşılığı olmayan konu → video çıkar, raporda listelenir — sebep: kullanıcı "diğer kaynakları istemiyorum" dedi; git ile geri alınabilir.
- dioganos.github.io/mat202 linki kalır — sebep: video değil, kullanıcının kendi izleme kaydı.
- Push yok, yalnız yerel commit — sebep: dışarı çıkış onay ister.
- 72 ID'nin 67'si @Buders (oEmbed). Silinecek 5: `_uphT5ZOosY`, `G66M584ymP8`, `X9DLYZWjiJA` (1. hafta), `ERixPmLdaRc` (2. hafta), `VynRtL3I5bI` (5. hafta) — sebep: BUders dışı.
- Yerine bir şey eklenmez — sebep: 2'sinin BUders karşılığı (`X1oYUZppIjI`, `dwEZmv9YVU4`) aynı haftada zaten var; 3'ünün BUders'te videosu yok, en yakın `wGvNOMdedrk` listede.
- E içindeki 4 BUders "ek video" kaydı kalır — sebep: BUders kanalı.

## Kısıtlar
- Tek dosya: `index.html` (~108 KB, video verisi JS içinde, satır ~55-80).
- Önceki commit 90fa87e "Ek videolar BUders kaynaklarıyla değiştirildi" kısmen yaptı; 2. hafta ek konularında hâlâ youtu.be linkleri var.

## Dosya haritası
- `index.html:55` — hafta notları JSON içinde, "2. haftanın ek konuları" youtu.be linkleri
- `index.html:76-80` — video render: youtube-nocookie embed, "YouTube'da aç", watch_videos listesi

## Ajanlar

## Durum
Son tamamlanan: vize c240fa2 push; mat202 (C:\Users\emirc\Downloads\mat202\mat202, Dioganos/mat202) dcb90de push — 6. haftadan `UTVD3obsHuk`, `oKOsCvjTg3c`, `Hu6yqs0R7GA` silindi. İki canlı sayfada 8 ID'nin hiçbiri yok (curl).
BUders'te Gauss kuadratür videosu yok; yazılı sayfa var: https://www.buders.com/altsayfa/gauss_kuadraturu.html
Sıradaki: kullanıcı isterse mat202 6. hafta notuna bu linki eklemek.
