# Mendora.AI - Kişisel Zindelik Takip Uygulaması

## Proje Genel Bakışı

Mendora.AI, kullanıcıların günlük günlük tutma, otomatik analiz ve pozitif pekiştirme yoluyla duygusal zindeliklerini izlemelerine yardımcı olmak için tasarlanmış hibrit bir yapay zeka destekli web uygulamasıdır. Kişiselleştirilmiş geri bildirim ve içgörüler sağlamak için kural tabanlı anahtar kelime analizini Google'ın Gemini Flash 2.5 API'si ile birleştirir.

**Hedef Kullanıcılar:**
- Daha iyi duygusal farkındalık arayan bireyler
- Günlük ruh hali düzenlerini takip etmek isteyen kişiler
- Farkındalık alışkanlıkları geliştirmek isteyen kullanıcılar
- Zaman içinde duygusal kalıplarını takip etmek isteyen herkes

**Ele Alınan Sorunlar:**
- **Negatif Düşünce Kalıpları**: Anahtar kelime analizi yoluyla yinelenen temaları belirlemeye yardımcı olur.
- **Günlük Stres**: Anında geri bildirim ve başa çıkma stratejileri sağlar.
- **Öz Farkındalık Eksikliği**: Tutarlı takip ve yansıma yoluyla öz farkındalığı artırır.
- **Kişisel Gelişim**: Öz yansıma için özel, yargılamayan bir ortam sunar.

## Özellikler

Mendora.AI, duygusal zindeliği desteklemek için bir dizi özellik sunar:

1.  **Günlük Modülü (`pages/journal.py`)**: Kullanıcıların günlük düşüncelerini ve duygularını yazmalarına olanak tanır, bunlar daha sonra anında geri bildirim için kural tabanlı ve yapay zeka destekli analizlerle işlenir.
2.  **Yapay Zeka Geri Bildirim Sistemi (`utils/ai_feedback.py`)**: Gelişmiş duygu analizi, kişiselleştirilmiş öneriler ve duygu tespiti için Google Gemini Flash 2.5 API ile entegre olur.
3.  **Günlük Olumlamalar (`pages/affirmations.py`)**: Her gün yeni pozitif olumlamalar gösterir, görüntülenen mesajları tekrarlamamak için bir mekanizma içerir.
4.  **Ölçümler Paneli (`pages/measurements.py`)**: Tarihsel günlük girişlerinin, analiz sonuçlarının ve zaman içindeki ruh hali trendlerinin görsel bir özetini sunar.

## Teknik Mimari

### Temel Teknolojiler
-   **Ön Uç**: Streamlit (Python tabanlı web çerçevesi)
-   **Yapay Zeka Entegrasyonu**: Google Gemini Flash 2.5 API (`google-generativeai` aracılığıyla)
-   **Veritabanı**: SQLite (geliştirme/Streamlit Cloud geçici depolama için)
-   **Veri Manipülasyonu**: Pandas
-   **Grafikler**: Plotly Express
-   **Kimlik Doğrulama**: Streamlit'in yerleşik oturum durumu yönetimi
-   **Belge İşleme (Gelecek/Planlanan)**: `pypdf`, `langchain`, `chromadb`, `sentence-transformers` (PDF analizi, vektör veritabanları için)

### Hibrit Yapay Zeka Yaklaşımı
-   **Yerel İşleme**: Temel anahtar kelime eşleştirme, basit kategorizasyon, veri doğrulama.
-   **Bulut İşleme**: Karmaşık duygu analizi, Gemini API aracılığıyla kişiselleştirilmiş öneriler.
-   **Karar Mantığı**: Basit kategorizasyonlar yerel olarak ele alınır; karmaşık analizler API'ye gönderilir.

-   ## 🚀 Gelecek Planları ve Entegrasyonlar

Mendora.AI'yi sürekli geliştirmeyi ve kullanıcılara daha kapsamlı bir zindelik deneyimi sunmayı hedefliyoruz. İşte gelecekteki potansiyel entegrasyonlarımız ve bu geliştirmelerde kullanılabilecek teknolojiler:

### 1. Ortam Sesi Analizi ve Yapay Zeka Geri Bildirimi

*   **Amaç:** Kullanıcının çevresel sesleri analiz ederek ruh hali ve stres seviyesi üzerindeki çevresel faktörlerin etkisini anlamak. Örneğin, gürültülü bir ortamın stresi artırıp artırmadığını tespit etmek veya doğa seslerinin rahatlatıcı etkisini belgelemek.
*   **Teknolojiler:**
    *   **Ses İşleme Kütüphaneleri:** `librosa` ve `pydub` (ses verisi işleme, özellik çıkarma ve analiz için).
    *   **Gerçek Zamanlı Ses Yakalama:** `streamlit_webrtc` (web tabanlı ses girişi ve işleme için).
    *   **Yapay Zeka Modelleri:** Çevresel ses sınıflandırması (örneğin, gürültü seviyesi, insan konuşması, doğa sesleri gibi belirli ses ortamlarını tanıma), sesin duygusal tonunu ve stres göstergelerini analiz etmek için özel eğitilmiş veya genel ses analizi API'leri (örn. Google Cloud Speech-to-Text, Google Cloud Natural Language API'nin sesle ilgili uzantıları veya özel makine öğrenimi modelleri).

### 2. BDT (Bilişsel Davranışçı Terapi) ve Günlük Testler

*   **Amaç:** Kullanıcılara BDT prensiplerine dayalı yönlendirilmiş testler, egzersizler ve değerlendirmeler sunarak olumsuz düşünce kalıplarını tanımalarına ve daha sağlıklı düşünce biçimleri geliştirmelerine yardımcı olmak. Düzenli testlerle ilerlemeyi izlemek.
*   **Teknolojiler:**
    *   **Veritabanı Yapısı:** Test sorularını, kullanıcı yanıtlarını, skorları ve zaman içindeki ilerlemeyi depolamak için mevcut SQLite yapısının genişletilmesi (veya Firebase gibi üretim veritabanlarıyla entegrasyon).
    *   **Kullanıcı Arayüzü:** Streamlit'in form bileşenleri, etkileşimli öğeler ve görselleştirme yetenekleri kullanılarak sezgisel test arayüzlerinin oluşturulması.
    *   **Yapay Zeka Destekli Analiz ve Kişiselleştirme:** Kullanıcının test yanıtlarını değerlendirmek, bilişsel çarpıtmaları tespit etmek ve kişiselleştirilmiş BDT alıştırmaları, okuma materyalleri veya geri bildirimler sunmak için Gemini API veya ince ayarlanmış (fine-tuned) modellerin kullanılması.
    *   **Mantık Geliştirme:** Test puanlama algoritmaları, sonuç yorumlama motoru ve kullanıcının yanıtlarına göre sonraki adımları önerme için Python tabanlı iş mantığı.

### 3. Belge İşleme ve Bilgi Çağırma Sistemi

*   **Amaç:** Kullanıcıların PDF gibi belgeleri yüklemesine olanak tanıyarak bu belgelerden bilgi çekme ve bu bilgiler üzerinden sorulara yanıt verme veya önerilerde bulunma yeteneği. Örneğin, kişisel gelişim kitaplarından anahtar çıkarımlar yapmak veya akademik makalelerden özetler sunmak.
*   **Teknolojiler:**
    *   **Belge Yükleme ve Çıkarma:** `pypdf` veya benzeri kütüphaneler (PDF içeriğini metne dönüştürmek için).
    *   **Metin Parçalama (Chunking):** `langchain` (uzun belgeleri yönetilebilir parçalara bölmek için).
    *   **Vektör Veritabanı (Vector Database):** `Chroma` veya `FAISS` gibi vektör veritabanları (metin parçalarının gömülü temsillerini depolamak ve hızlı benzerlik aramaları yapmak için).
    *   **Gömme Modelleri (Embedding Models):** `sentence-transformers` veya Google'ın kendi gömme modelleri (metin parçalarını sayısal vektörlere dönüştürmek için).
    *   **Bilgi Çağırma ve Yanıtlama:** Kullanıcının sorgusuna göre vektör veritabanında en alakalı parçaları bulmak ve bu parçaları kullanarak Gemini API aracılığıyla kapsamlı ve bağlamsal yanıtlar oluşturmak (Retrieval-Augmented Generation - RAG yaklaşımı).

## Yerel Kurulum ve Çalıştırma

Mendora.AI'yi yerel makinenizde çalıştırmak için şu adımları izleyin:

1.  **Depoyu Klonlayın:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
    cd YOUR_REPOSITORY_NAME/mendora-ai
    ```
    *(YOUR_USERNAME ve YOUR_REPOSITORY_NAME değerlerini gerçek GitHub kullanıcı adınız ve depo adınızla değiştirin.)*

2.  **Sanal Ortam Oluşturun (Önerilir):**
    ```bash
    python -m venv venv
    # Windows'ta:
    .\venv\Scripts\activate
    # macOS/Linux'ta:
    source venv/bin/activate
    ```

3.  **Bağımlılıkları Yükleyin:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Gemini API Anahtarını Ayarlayın:**
    Uygulama Google Gemini Flash 2.5 API'yi kullanır. Google AI Studio'dan bir API anahtarı edinmeniz gerekir.
    *   [Google AI Studio](https://aistudio.google.com/app/apikey) adresini ziyaret edin.
    *   Bir API anahtarı oluşturun.
    *   Bu API anahtarını `GEMINI_API_KEY` adlı bir ortam değişkeni olarak ayarlayın.
        *   **Windows (Komut İstemi için):**
            ```cmd
            set GEMINI_API_KEY=API_ANAHTARINIZ
            ```
        *   **Windows (PowerShell için):**
            ```powershell
            $env:GEMINI_API_KEY="API_ANAHTARINIZ"
            ```
        *   **macOS/Linux için:**
            ```bash
            export GEMINI_API_KEY="API_ANAHTARINIZ"
            ```
        *(API_ANAHTARINIZ yerine gerçek Gemini API anahtarınızı yapıştırın. Kalıcı kurulum için bunu sisteminizin ortam değişkenlerine veya kabuk profil dosyanıza (.bashrc, .zshrc vb.) ekleyin.)*

5.  **Uygulamayı Çalıştırın:**
    ```bash
    streamlit run app.py
    ```
    Bu, uygulamayı varsayılan web tarayıcınızda (genellikle `http://localhost:8501` adresinde) açacaktır.

## Kullanım

1.  **Giriş / Kayıt:** Uygulamayı başlattığınızda, giriş yapmanız veya kaydolmanız istenecektir. Yeni bir kullanıcıysanız, bir hesap oluşturun.
2.  **Ana Sayfa:** Başarılı bir girişten sonra, "Ana Sayfa"ya yönlendirileceksiniz. Buradan farklı modüllere gidebilirsiniz:
    *   **📝 Günlüğüm**: Günlük düşüncelerinizi yazın ve yapay zeka destekli içgörüler alın.
    *   **✨ Olumlamalar**: Her gün yeni bir pozitif olumlama alın.
    *   **📈 Ölçümlerim**: Tarihsel günlük girişlerinizi görüntüleyin ve ruh hali trendlerini analiz edin.

## Streamlit Cloud Üzerinde Dağıtım

Mendora.AI'yi Streamlit Cloud'a dağıtmak için şu adımları izleyin:

1.  **Kodun GitHub'da olduğundan emin olun:** `requirements.txt` dahil olmak üzere tüm `mendora-ai` projeniz bir GitHub deposuna aktarılmış olmalıdır.
2.  **Streamlit Cloud'a gidin:** [Streamlit Cloud](https://streamlit.io/cloud) adresini ziyaret edin ve GitHub hesabınızla giriş yapın.
3.  **Yeni Bir Uygulama Dağıtın:**
    *   "New app" veya "Deploy an app" butonuna tıklayın.
    *   GitHub deponuzu seçin.
    *   "Main file path" için, GitHub'daki `app.py` dosyanızın doğrudan URL'sini sağlayın. Şuna benzer görünecektir: `https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME/blob/main/mendora-ai/app.py`
    *   "Advanced settings" -> "Secrets" altında, `GEMINI_API_KEY`'inizi bir sır olarak ekleyin. Bu, yapay zeka işlevselliği için çok önemlidir.
        *   Format şöyle olmalıdır:
            ```
            GEMINI_API_KEY="GERÇEK_GEMINI_API_ANAHTARINIZ"
            ```
    *   "Deploy!" butonuna tıklayın!

## Katkı

Mendora.AI'ye katkıda bulunmaktan memnuniyet duyarız! Nasıl katkıda bulunacağınızla ilgili yönergeler için lütfen [CONTRIBUTING.md](CONTRIBUTING.md) dosyasını (oluşturulacak) inceleyin.

## Lisans

Bu proje [MIT Lisansı](LICENSE) (oluşturulacak) altında lisanslanmıştır.

## İletişim

Herhangi bir soru veya destek için lütfen GitHub deposunda bir sorun (issue) açın.

---

**Mendora.AI** - Akıllı analiz ve pozitif pekiştirme yoluyla ruh sağlığı farkındalığını güçlendirmek.# mendora-ai-landingpage
