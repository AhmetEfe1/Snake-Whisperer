# Snake Whisperer - Game Design Document (GDD)

## 1. Proje Künyesi ve Genel Bakış
* **Proje Adı:** Snake Whisperer
* **Geliştirici:** Ahmet Efe Duman
* **Rol:** Solo Developer (Game Design, Programming, Audio/Hardware Integration)
* **Tür:** Eğitici Ritim / Keşif Macera
* **Hedef Platform:** PC (Windows)
* **Geliştirme Ortamı:** Unity 6 LTS (Universal 2D) & C#
* **Kontrol Yöntemi:** Blok Flüt (Akustik Frekans Algılama / Modifiye Fiziksel Kontrolcü)

---

## 2. Temel Konsept ve Çıkış Noktası
Snake Whisperer, geleneksel "Yılan Oynatıcısı" (Snake Charmer) kültürel temasını modern oyun dinamikleriyle birleştiren bir eğitim-ritim oyunudur. Oyuncu, klasik kontrol cihazları (klavye/mouse/gamepad) yerine gerçek bir nefesli enstrüman olan blok flütü üfleyerek çıkardığı notalarla oyunu deneyimler. Proje, temel müzik ve solfej eğitimini interaktif, eğlenceli ve refleksif bir oyun döngüsüne dönüştürmeyi hedefler.

---

## 3. Oynanış Mekanikleri (Gameplay Mechanics)

Oyun iki ana fazdan oluşan döngüsel bir yapıya sahiptir:

### A. Açık Dünya / Keşif Modu (Overworld)
* **Kamera:** Minimalist 2D Top-Down (Yukarıdan bakış) bakış açısı.
* **Yönlendirme:** Oyuncunun nefes eşiğini yormamak adına hareket mekaniği sade tutulur. Temel yön geçişleri ve akıcı hareketler hedeflenir.
* **Hedef:** Harita üzerinde dolaşarak farklı canlıları (tavşan, kurbağa vb.) keşfetmek ve karşılaşma tetiklemek.

### B. Karşılaşma ve Ritim Modu (Avlanma / Savaş Fazı)
* **Mekanik İlhamı:** *Undertale* karşılaşma dinamikleri ile *Guitar Hero* ritim/zamanlama mekaniğinin hibriti.
* **Arayüz:** Hedefe doğru belirli bir tempoda akan nota göstergeleri (Timeline / Müzik Portesi).
* **Etkileşim:** 
  * Oyuncu, akan notalar vuruş çizgisine ulaştığında flüt ile doğru notayı (Do, Re, Mi vb.) üfler.
  * Doğru zamanlama ve frekans eşleşmesi yılanın hipnoz göstergesini doldurur.
  * Hatalı notalar veya kaçırılan vuruşlar hedefin kaçma riskini artırır.
  * Melodi başarıyla tamamlandığında av yakalanır ve bölüm tamamlanır.

---

## 4. Eğitici Boyut (Pedagojik Hedefler)
* **İşitsel Farkındalık:** Farklı ses frekanslarını ve oktavları kulaktan ayırt edebilme.
* **Pratik Solfej Becerisi:** Ekranda beliren nota sembollerini ezber yerine oyun refleksleriyle doğru enstrüman pozisyonuna dönüştürebilme.
* **Ritim ve Koordinasyon:** Belirli bir BPM (tempo) aralığında nefes ve parmak koordinasyonunu geliştirme.

---

## 5. Teknik Altyapı ve Kontrolcü Mimarisi
Projenin girdi sistemi modüler olarak planlanmıştır:

* **Yaklaşım 1 (Yazılımsal Akustik Analiz - FFT):** Standart blok flütten çıkan akustik sesin Unity içinde `AudioSource.GetSpectrumData` ile frekans spektrumuna (Fast Fourier Transform) ayrılması ve nota aralıklarına (Hz) göre girdi komutlarına dönüştürülmesi.
* **Yaklaşım 2 (Fiziksel Modifikasyon - Donanım Tabanlı):** Flüt gövdesine entegre kapasitif/dokunmatik sensörler veya mikro switch'ler ile nefes kanalına yerleştirilen üfleme/basınç algılayıcının bir mikrodenetleyici (Arduino) üzerinden Unity'ye serial veri veya HID klavye girdisi olarak aktarılması.

---

## 6. Geliştirme Takvimi ve Yol Haritası

| Hafta | Hedeflenen Çıktı / Milestones |
| :--- | :--- |
| **1. Hafta** | Repo kurulumu, Unity 2D boş proje ayarları ve GDD teslimi |
| **2. Hafta** | Girdi prototipi: Flüt sesinin/frekansının Unity'de algılanması |
| **3. Hafta** | Karşılaşma modu temel arayüzü (Akan nota çizelgesi ve vuruş algılama) |
| **4. Hafta** | Top-down yılan hareketi ve harita üzerinde av karşılaşma tetikleyicisi |
| **5. Hafta** | Karşılaşma sistemi ile nota girdisinin tam entegrasyonu |
| **6. Hafta** | Görsel/işitsel cilalama, hata ayıklama (debug) ve final jüri sunumu |