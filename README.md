# Akıllı Robot Projesi | Smart Robot Project

## 📌 Proje Tanımı | Project Description
Çoklu sensör entegrasyonlu akıllı robot kontrol sistemi. Engelden kaçma, çizgi takibi, sıcaklık ve gaz seviyesi ölçümü yapabilen otonom robot. | Smart robot control system with multiple sensor integration. Autonomous robot with obstacle avoidance, line tracking, temperature and gas level measurement.

## 🛠️ Donanım Özellikleri | Hardware Features
- **Motor Kontrol**: L298N sürücü ile 2x DC motor | 2x DC motors with L298N driver
- **Sensörler**:
  - 2x IR çizgi takip sensörü | 2x IR line tracking sensors
  - 3x HC-SR04 ultrasonik engel algılama | 3x HC-SR04 ultrasonic obstacle detection
  - DHT11 sıcaklık/nem sensörü | DHT11 temperature/humidity sensor
  - MQ-9 gaz sensörü | MQ-9 gas sensor
- **Görsel Uyarı Sistemi**: 6x LED (2 yeşil, 2 sarı, 2 kırmızı) | 6x LEDs (2 green, 2 yellow, 2 red)
- **Sesli Uyarı**: Pasif buzzer | Passive buzzer

## 🔌 Pin Bağlantıları | Pin Connections
| Bileşen | Pin | Component | Pin |
|---------|-----|-----------|-----|
| Motor ENA | 2 | Sol IR | 44 |
| Motor ENB | 3 | Sağ IR | 45 |
| Motor IN1 | 22 | Orta Trig | 37 |
| Motor IN2 | 23 | Orta Echo | 36 |
| Motor IN3 | 24 | Sağ Trig | 41 |
| Motor IN4 | 25 | Sağ Echo | 40 |
| DHT11 | 48 | Sol Trig | 32 |
| Buzzer | 10 | Sol Echo | 33 |
| Yeşil LED1 | 4 | Sarı LED1 | 6 |
| Kırmızı LED1 | 8 | Yeşil LED2 | 5 |
| Sarı LED2 | 7 | Kırmızı LED2 | 9 |
| MQ-9 Gaz | A0 | | |

## 🌟 Temel Fonksiyonlar | Core Functions
1. **Çizgi Takibi** | Line Following
   - IR sensörlerle siyah çizgi takibi
   - Otomatik yön düzeltme (sola/sağa dönüş)

2. **Engel Algılama ve Kaçınma** | Obstacle Detection & Avoidance
   - 3 yönlü ultrasonik tarama (ön, sağ, sol)
   - Akıllı kaçınma algoritması (geri dönüş + açılı hareket)

3. **Çevre İzleme** | Environment Monitoring
   - Gerçek zamanlı sıcaklık ölçümü (DHT11)
   - Gaz seviye tespiti (MQ-9)
   - Görsel/sesli uyarı sistemi (LED'ler + buzzer)

4. **Motor Kontrol** | Motor Control
   - İleri/geri hareket
   - 45° ve 90° dönüş fonksiyonları
   - Ayarlanabilir hız kontrolü

## ⚙️ Kurulum | Setup
1. Arduino IDE'yi yükleyin (v1.8+ önerilir) | Install Arduino IDE (v1.8+ recommended)
2. Gerekli kütüphaneleri ekleyin | Add required libraries:
   ```cpp
   #include <DHT.h>```

3. Donanım bağlantılarını şemaya göre yapın | Make hardware connections according to diagram

4. Kodu yükleyin ve seri monitörü açın (9600 baud) | Upload code and open serial monitor (9600 baud)

## ⚠️ Kalibrasyon ve Ayarlar | Calibration & Settings

Motor Hızları | Motor Speeds:

   ```cpp
analogWrite(ENA, 70); // Normal hız | Normal speed
analogWrite(ENA, 100); // Dönüş hızı | Turning speed
```


## Eşik Değerleri | Threshold Values:

   ```cpp
// Sıcaklık | Temperature
if (sicaklik > 32) // Alarm seviyesi | Alarm level

// Gaz | Gas
if (gazDegeri > 450) // Tehlikeli seviye | Dangerous level

// Engel | Obstacle
if (mesafeOrta < 25) // Engel algılama | Obstacle detection
```

## 📊 Seri Monitör Çıktısı | Serial Monitor Output

   ```cpp
Sol IR: 0 | Sag IR: 1 | Karar: SAĞA DÖN
Mesafe Orta: 15 cm
Sıcaklık: 26.5°C
Gaz: 320
```
## 📝 Önemli Notlar | Important Notes
Sensörlerin doğru çalışması için ortam ışığından uzak tutun | Keep away from direct light for proper sensor operation

Gaz sensörü ısınma süresi gerektirir (~24 saat) | Gas sensor requires warm-up time (~24 hours)

Yüksek sıcaklık (>32°C) ve gaz (>450) durumunda sistem alarm verir | System alarms when temperature >32°C or gas >450

