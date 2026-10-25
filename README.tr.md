# 🏎️ Desk Racer (Masaüstü Mikro Pist Yarışı)

[![Three.js](https://img.shields.io/badge/Three.js-r183-black?style=flat&logo=three.js)](https://threejs.org/)
[![Rapier 3D](https://img.shields.io/badge/Rapier_3D-v0.19-orange?style=flat)](https://rapier.rs/)
[![Vite](https://img.shields.io/badge/Vite-6.2-646CFF?style=flat&logo=vite)](https://vitejs.dev/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat&logo=typescript)](https://www.typescriptlang.org/)
[![Lisans: MIT](https://img.shields.io/badge/Lisans-MIT-green.svg)](LICENSE)

> **Tarayıcı üzerinde Three.js ve Rapier3D fizik motoruyla çalışan, 1:87 HO ölçekli minyatür masaüstü hız ve zaman karşıtı yarış simülasyonu.**

[English Documentation (README.md)](README.md)

---

## 📸 Genel Bakış

**Desk Racer**, sıcak gün batımı (golden hour) ışığıyla aydınlatılan gerçekçi bir çalışma masasında geçen yüksek tempolu bir mikro go-kart yarış oyunudur. Klavyelerin yanından süzülün, laptop sehpasının altından geçin, kahve kupasının etrafındaki spiral virajları dönün ve en iyi tur derecenizi elde edin.

### ✨ Temel Özellikler

- **1:87 HO Ölçekli Gerçekçi Fizik**: `@dimforge/rapier3d-compat` (WebAssembly) destekli; süspansiyon esnemesi, drift mekaniği, viraj tutunması ve yere basma kuvveti simülasyonu.
- **Sinematik Makro Fotoğrafçılık Görselleri**: 25-noktalı Vogel Spiral Bokeh lens simülasyonu (tilt-shift makro alan derinliği), ACES Filmic ton eşleme ve Unreal Bloom ışıma efektleri.
- **Dinamik Prosedürel Ses Sistemi (Web Audio API)**: Motor devrine göre dinamik sentezlenen sesler, egzoz patlamaları, bordür titreşimleri ve lastik drift gıcırtıları.
- **4 Farklı Kamera Modu**:
  1. **Takip Kamerası (1)**: Yumuşak yaylı sönümlemeli klasik 3. şahıs yarış görünümü.
  2. **Kokpit / Kask Vizörü (2)**: Siperlik çerçeveli sürükleyici 1. şahıs pilot görüşü.
  3. **Tüm Masa Görünümü (3)**: Tüm çalışma masasını ve pisti izleyen izometrik makro kamera.
  4. **Dron Kamerası (4)**: Kartı serbestçe takip eden sinematik izleyici dronu.
- **Canlı Vektörel HUD Arayüzü**:
  - Dinamik neon aydınlatmalı açılı SVG takometre / hız göstergesi.
  - Canlı kart konumunu anlık gösteren 3D eğimli pist mini haritası.
  - Tur sayacı, milisaniye hassasiyetli kronometre, sektör zaman farkları ve F1 5'li kalkış ışıkları.
- **Otopilot Modu**: Klavyeden `P` tuşuna basarak aracın ideal yarış çizgisinde kendi kendine sürüşünü izleyebilirsiniz.
- **Mobil Dokunmatik Kontroller**: Telefon ve tablet ekranlarında otomatik beliren sanal yön ve gaz/fren pedalları.

---

## 🎮 Kontroller

### Masaüstü Klavye

| Tuş | İşlev |
|:---:|:---|
| <kbd>W</kbd> veya <kbd>↑</kbd> | Gaz (İleri) |
| <kbd>A</kbd> veya <kbd>←</kbd> | Sola Dönüş |
| <kbd>D</kbd> veya <kbd>→</kbd> | Sağa Dönüş |
| <kbd>S</kbd> veya <kbd>↓</kbd> | Fren / Geri Vites |
| <kbd>1</kbd> | Takip Kamerası (Chase) |
| <kbd>2</kbd> | Kokpit / Vizör Kamerası (Cockpit) |
| <kbd>3</kbd> | Tüm Masaüstü Görünümü (Desk View) |
| <kbd>4</kbd> | Dron Kamerası (Drone View) |
| <kbd>P</kbd> | Otopilot Aç / Kapat |
| <kbd>M</kbd> | Sesi Aç / Kapat (Mute) |
| <kbd>Enter</kbd> | Yarışı Başlat / Yeniden Başlat |

### Mobil / Dokunmatik Ekranlar
Dokunmatik ekranlı bir cihazda açıldığında sol altta sanal direksiyon okları (**SOL** / **SAĞ**), sağ altta ise pedallar (**GAZ** / **FREN**) görüntülenir.

---

## 🛠️ Teknoloji Yığını & Mimari

- **Görselleştirme**: [Three.js](https://threejs.org/) (WebGL, PCF Soft Gölgeler, PMREM yansımaları, özel post-processing geçişleri).
- **Fizik**: [Rapier3D](https://rapier.rs/) (`@dimforge/rapier3d-compat`) WebAssembly tabanlı fizik motoru.
- **Post-Processing**: `EffectComposer`, `RenderPass`, `UnrealBloomPass`, `OutputPass`, `BokehPass` (Vogel Spiral).
- **Ses**: Web Audio API sentezleyicisi ve stereo ses döngüleri.
- **Derleme Aracı**: [Vite 6](https://vitejs.dev/).
- **Diller**: JavaScript (ESNext modülleri) & TypeScript.

---

## 📂 Dizin Yapısı

```
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md        # Hata bildirim şablonu
│   │   └── feature_request.md   # Özellik öneri şablonu
│   ├── workflows/
│   │   └── ci.yml               # GitHub Actions CI doğrulama iş akışı
│   └── PULL_REQUEST_TEMPLATE.md # PR kontrol listesi
├── public/
│   └── assets/
│       ├── audio/               # Motor ve ortam ses dosyaları
│       └── data/                # Pist rotası verileri ve masa konfigürasyonu
├── src/
│   ├── audio/
│   │   └── WebAudioSynth.js     # Prosedürel ses sentezleme motoru
│   ├── physics/
│   │   └── KartPhysicsController.js # Rapier3D araç fizik mekaniği
│   ├── scene/
│   │   ├── CoasterTrackBuilder.js   # Pist geometrisi ve ray oluşturucu
│   │   ├── DeskDioramaBuilder.js    # Masaüstü aksesuarları ve materyalleri
│   │   ├── GoldenHourAtmosphere.js  # Işıklandırma, güneş açısı ve hacimsel sis
│   │   ├── MicroKartBuilder.js      # 1:87 ölçekli go-kart 3D modeli
│   │   ├── ProceduralTextures.js    # Prosedürel doku üreteçleri
│   │   └── RoomEnvironmentBuilder.js# Oda duvarları ve çevre ışığı
│   ├── App.tsx
│   ├── main.js                  # Three.js ana render döngüsü, HUD ve kontroller
│   ├── main.tsx
│   └── style.css                # Arayüz ve HUD CSS stilleri
├── .gitignore
├── CONTRIBUTING.md              # Katkı sağlama kılavuzu
├── LICENSE                      # MIT Lisansı
├── package.json
├── README.md                    # İngilizce ana dokümantasyon
├── README.tr.md                 # Türkçe dokümantasyon
├── tsconfig.json
└── vite.config.ts
```

---

## 🚀 Kurulum ve Çalıştırma

### Gereksinimler

- [Node.js](https://nodejs.org/) (v18.0.0 veya üzeri)
- `npm`, `pnpm` ya da `bun` paket yöneticisi

### Adım Adım Kurulum

1. **Depoyu klonlayın:**
   ```bash
   git clone https://github.com/KULLANICI_ADINIZ/desk-racer.git
   cd desk-racer
   ```

2. **Bağımlılıkları yükleyin:**
   ```bash
   npm install
   ```

3. **Geliştirme sunucusunu başlatın:**
   ```bash
   npm run dev
   ```
   Tarayıcınızda `http://localhost:3000` adresine gidin.

### Canlıya Alma (Production Build)

Optimize edilmiş üretim dosyalarını oluşturmak için:
```bash
npm run build
```

Oluşturulan derlemeyi yerel olarak test etmek için:
```bash
npm run preview
```

### Kod Denetimi (Lint / TypeCheck)

```bash
npm run lint
```

---

## 🤝 Katkıda Bulunma

Projeye katkı sağlamak, hata bildirmek veya yeni özellikler önermek çok değerlidir!
Lütfen [CONTRIBUTING.md](CONTRIBUTING.md) dosyasını inceleyin.

---

## 📄 Lisans

Bu proje açık kaynaklı olup [MIT Lisansı](LICENSE) altında dağıtılmaktadır. Kodları kişisel veya ticari projelerinizde dilediğiniz gibi kullanabilir, değiştirebilir ve genişletebilirsiniz.
