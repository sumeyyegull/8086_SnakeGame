# 8086 Snake Game (Yılan Oyunu)

Bu proje, Intel 8086 mikroişlemcisi üzerinde Assembly dili kullanılarak geliştirilmiş klasik bir Yılan Oyunu uygulamasıdır.  
Oyun, Proteus simülasyonu ile çalıştırılmakta olup, grafiksel gösterim 8x8 LED Dot Matrix, skor ve durum bilgileri ise LM016L 16x2 LCD ekran üzerinden sağlanmaktadır.

Repoda iki farklı versiyon bulunmaktadır:
- Versiyon 1 – Harici RAM/ROM içermeyen temel Proteus simülasyonu (klasör: 8086_Snake_Game)
  
  <img width="1579" height="426" alt="Ekran görüntüsü 2026-01-06 134402" src="https://github.com/user-attachments/assets/137c9bcf-fdf2-4aef-9635-f05058d3b986" />

- Versiyon 2 – Harici RAM & ROM ile tam donanım simülasyonu (klasör: Ramli Proje)
  
<img width="1800" height="677" alt="Ekran görüntüsü 2026-01-06 142531" src="https://github.com/user-attachments/assets/688dea0b-142c-48aa-bef5-7c4a01d9f98f" />

## Proje Amacı

Projenin temel hedefleri şunlardır:
- Intel 8086 mikroişlemcisi ile interaktif bir Yılan Oyunu oluşturmak
- Yılanın hareketlerini yön butonları ile kontrol etmek
- Oyun skorunu gerçek zamanlı olarak LCD ekran üzerinden göstermek
- Mikroişlemci tabanlı sistemlerde donanım-yazılım entegrasyonunu uygulamalı olarak göstermek

## Proje Konusu (Versiyon 1)

Yılan Oyunu, 8x8 LED Dot Matrix paneli üzerinde görselleştirilir.  
Kullanıcı, UP, DOWN, LEFT, RIGHT yön butonları ile yılanın hareketini kontrol eder.

Oyun sırasında:
- Yemler rastgele oluşturulur
- Yılan yemi yedikçe boyu uzar
- Skor bilgisi gerçek zamanlı olarak LCD ekranda güncellenir

Temel bileşenler:
- 8086 mikroişlemci
- 8255A Programlanabilir G/Ç Arayüzü (PPI)
- 74LS373 adres latch

## Kullanılan Donanım Bileşenleri

- Intel 8086 Mikroişlemci – Oyunun algoritmalarını yürütür ve çevre birimlerini kontrol eder
- 8255A Programlanabilir Çevresel Arayüz (PPI) – Mikroişlemci ile LCD, Dot Matrix ve butonlar arasında veri akışını sağlar
- 74LS373 Latch – 8086’nın çoklamalı adres/veri hattını ayrıştırır
- 8x8 LED Dot Matrix Panel – Yılan ve yemlerin grafiksel gösterimi
- LM016L 16x2 LCD Ekran – Skor ve oyun durumlarını metin tabanlı olarak gösterir
- Yön Butonları (UP, DOWN, LEFT, RIGHT) – Kullanıcı girişlerini sağlar

## 8255A Port Yapılandırması (Mode 0)

- Port A (PA0–PA7) – LCD veri hattı (D0–D7) ve LED Dot Matrix satır kontrolü
- Port B (PB0–PB7) – LED Dot Matrix sütun kontrolü
- Port C
  - PC0–PC3: Yön butonları girişleri
  - PC4 (RS): LCD Register Select
  - PC5 (E): LCD Enable

## Kullanılan Yazılım Araçları

- EMU8086 – Assembly kodlarının yazılması, derlenmesi ve test edilmesi
- Proteus – Donanım tasarımının simülasyonu (Versiyon1 ve Versiyon2 klasörlerinde dosyalar)
- 8086 Assembly Dili – Oyun algoritması, buton okuma, skor hesaplama, LCD kontrolü, LED matris çoklama

## Oyun Çalışma Mantığı

1. Başlangıç – Yılan uzunluğu 3, LCD’de başlangıç skoru gösterilir
2. Giriş Tarama (Polling) – Yön butonları sürekli izlenir, yılanın hareket yönü güncellenir
3. Görüntüleme ve Oyun Mantığı – LED Dot Matrix çoklama ile sürülür, yılanın gövdesi güncellenir, yem yendiğinde skor artar
   - Yılan kendi gövdesine çarptığında: LCD’de “GAME OVER” mesajı ve LED matris yanıp sönme efekti

## Çalışma Anı 

Aşağıdaki ekran görüntüsü, oyunun Proteus simülasyonu sırasında çalışırken nasıl göründüğünü göstermektedir.  
Yılan, LED Dot Matrix üzerinde hareket ederken skor ve oyun durumu LCD ekranda görüntülenmektedir.

<img width="309" height="398" alt="Ekran görüntüsü 2026-01-29 133540" src="https://github.com/user-attachments/assets/a09e1cbe-4d6b-4f41-be75-78875fe4709c" />


## Simülasyon Notları

- Versiyon 1 – Harici RAM/ROM yok, Proteus’un dahili belleği kullanılır
- Versiyon 2 – Harici RAM & ROM ile tam donanım simülasyonu
- Simülasyon kararlılığı yüksek, donanım-yazılım etkileşimi net olarak gözlemlenebilir

## Notlar

- Proje eğitim ve akademik amaçlıdır
- Proteus dosyaları referans olarak repo içindeki klasörlerde mevcuttur

## Geliştirici

Proje, 8086 Mikroişlemci dersi kapsamında Assembly dili ve Proteus simülasyonu kullanılarak geliştirilmiştir.
