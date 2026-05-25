# Opsiyon İşlemleri 101 - Premium Academy Tasarım Dokümanı (Spec)

## Genel Bakış
Bora Özkent Academy'ye ait "Opsiyon İşlemleri 101" eğitim sayfası, kullanıcıların karmaşık finans dünyasını 5 kısa derste öğrenebilecekleri, NotebookLM'den çekilen zenginleştirilmiş içerikle desteklenen tek sayfalık (SPA benzeri) interaktif bir web sitesidir. Tasarım, "Masterclass" benzeri premium, ciddi ve okunaklı bir akademi deneyimi sunmayı hedefler.

## Mimari ve Teknoloji Yığını
- **Core:** Sadece HTML ve Vanilla JS (build adımı olmadan çalışacak tek sayfalık yapı).
- **Styling:** Tailwind CSS V3 (CDN üzerinden).
- **Karanlık/Aydınlık Tema:** Tailwind `darkMode: 'class'` konfigürasyonu ile `localStorage` destekli tema yönetimi.

## Tasarım Yönergeleri (Premium Academy Stili)
- **Renk Paleti:**
  - Aydınlık (Light): `bg-slate-50`, metinler `text-slate-800`.
  - Karanlık (Dark): `bg-slate-950`, metinler `text-slate-200`.
  - Vurgular: Şık ve ciddi bir etki için Zümrüt Yeşili (Emerald) ve Koyu Lacivert/İndigo tonları.
- **Tipografi:** 
  - Başlıklar için Premium Serif font: `Playfair Display`.
  - Gövde metinleri için yüksek okunabilirlik sunan Sans-serif font: `Inter`.
- **UI Elementleri:** 
  - Yuvarlatılmış köşeler (`rounded-2xl` ve `rounded-3xl`).
  - İnce ve zarif kenarlıklar, yumuşak gölgeler.

## Bileşenler (Components)

### 1. Navigasyon ve Header (Sticky)
- **Sol:** Logo ve "Bora Özkent Academy" metni.
- **Sağ:** Karanlık/Aydınlık tema geçiş butonu (Güneş/Ay ikonları animasyonlu).
- **Alt:** Kullanıcının okuma yüzdesini gösteren ince, şık bir `progress-bar`.

### 2. İçindekiler (Sidebar & Mobil Navigasyon)
- **Masaüstü:** Sol tarafa sabitlenmiş (sticky) menü. Okunan ders aktif olarak vurgulanacak (IntersectionObserver kullanılarak).
- **Mobil:** Üstte yatay kaydırılabilir (horizontal scroll) sekmeler.

### 3. Ders Bölümleri (1'den 5'e kadar)
Her bir ders (Section) aşağıdaki yapıdan oluşacaktır:
1. **Ders Başlığı ve Özeti:** 
   - İlgili numara ve Playfair Display ile yazılmış şık bir başlık.
   - Giriş mahiyetinde, büyük puntolu özet metni.
2. **Kilit Kavramlar (İnteraktif Flip-Kartlar):**
   - Kullanıcının önceki sürümde beğendiği 3D dönme efektli (Flip Card) yapı, premium tasarıma uygun şekilde yeniden kodlanacak. Kartın ön yüzünde terim adı, arkasında kısa tanım yer alacak. Hover durumunda zarif bir animasyonla dönecek.
3. **Detaylı Açıklama:** 
   - Klasik akordeonlar (gizli içerik) yerine, editoryal bir okuma deneyimi sunmak adına doğrudan sayfada sergilenen zengin metin (Typography plugin benzeri `prose` sınıfları) kullanılacak. Önemli uyarılar, sol kenarlıklı şık bir blokıntı (blockquote) içinde verilecek.
4. **Gerçek Hayat Örneği:** 
   - Metinden ayrışan, özel arka plana sahip, içerisine ilgili bir ikon veya küçük bir emoji eklenmiş "Callout" (vurgu) kutuları şeklinde tasarlanacak.

### 4. Footer
- Bora Özkent Academy logosu.
- Telif uyarıları ("Bora Özkent Academy - 2026").
- Basit, sade kapanış.

## Veri Akışı
Tüm içerikler doğrudan dosyaya gömülü (hardcoded) olacaktır. NotebookLM'den çekilen ders içerikleri (1. Opsiyon Nedir?, 2. Call/Put, 3. Strike Price, 4. Expiration, 5. Premium & Greeks) HTML içine semantic etiketlerle (`<section>`, `<article>`, `<aside>`) yerleştirilecektir.

## Test ve Kriterler
- Mobil ve masaüstü uyumluluğu kontrol edilecek.
- Karanlık tema geçişinde metin/arka plan kontrast sorunları yaşanmayacak.
- Flip-kartlar mobil cihazlarda dokunma (tap) ile düzgün dönecek.
- Sayfa kaydırıldıkça "İçindekiler" menüsü aktif başlığı doğru vurgulayacak.
