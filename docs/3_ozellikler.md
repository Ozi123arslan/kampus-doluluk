# 3. Özellikler

Uygulamanın altı zorunlu özelliği var ve her biri dersin bir konusunu karşılıyor.

| # | Özellik | Ders konusu | Kullanıcı ne yapar |
| --- | --- | --- | --- |
| 1 | Ekranlar arası geçiş: mekan listesi, mekan detayı, bildirim paneli, giriş/kayıt, profil | Navigasyon | Listeden bir mekana dokunur, detayına gider, oradan bildirim panelini açar; alt menüden profile geçer |
| 2 | Okul e-postasıyla giriş ve canlı doluluk | Firebase (Auth + Firestore) | `@std.yildiz.edu.tr` adresiyle kayıt olur ve e-postasını doğrular; bir öğrencinin bildirimi diğer telefonlarda anında görünür |
| 3 | İnternetsiz son bilinen durum | Yerel DB (Hive) | İnternet yokken mekanların son durumunu "12 dk önce" etiketiyle görür |
| 4 | Hava durumuna göre uyarı | API / JSON (Open-Meteo) | Yağmurlu havada açık alanlı mekanların önerilmediğini listenin üstünde görür |
| 5 | Doluluk göstergesi geçişleri | Animasyon | Bir mekanın durumu değiştiğinde gösterge rengi ve doluluk çubuğu yumuşakça değişir |
| 6 | Her ekranın mantığı ayrı bir ViewModel'de | MVVM + Riverpod | (Görünmez) Ekranlar yalnızca çizer; hesaplama ve veri işleri ViewModel'de yapılır |

## Kullanım kuralları

- **Bakmak serbest:** Mekanların durumunu görmek için giriş gerekmez.
- **Bildirim için doğrulanmış okul e-postası:** Bildirim yalnızca e-postasını doğrulamış `@std.yildiz.edu.tr` hesaplarıyla yapılabilir. Kural hem uygulamada hem Firestore güvenlik kurallarında uygulanır.
- **Mekanda olma şartı:** Bildirim butonu yalnızca kullanıcı mekana 100–150 metreden yakınsa çalışır (GPS). Sunum için ayarlarda bu kontrolü kapatan bir demo modu vardır.
- **Sıklık sınırı:** Aynı kişi aynı mekana 15 dakikada en fazla bir bildirim yapabilir.
- **Üç seviye:** Bildirim seçenekleri Boş, Orta ve Dolu'dur.

## Mekanlar

Davutpaşa Kampüsü'ndeki 8 mekan: Hokka Cafe, Kayıntı Cafe, Büyük Ev Cafe, Yıldız Cafe, 21co, YTÜ Yemekhane (alt kat), YTÜ Yemekhane (üst kat), YTÜ Spor Salonu. Liste sabittir; kullanıcı mekan ekleyemez. Yemekhanenin iki katı listede tek kartta iki satır olarak gösterilir.

## Sonraki sürümler için

Saatlik yoğunluk grafiği ("genelde 12:30'da dolu") MVP'ye alınmadı; anlamlı olması için haftalarca veri birikmesi gerekiyor.
