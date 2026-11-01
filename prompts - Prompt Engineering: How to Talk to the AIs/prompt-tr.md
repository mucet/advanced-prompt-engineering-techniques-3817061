# Prompt Engineering: How to Talk to the AIs — Detaylı Eğitim Özeti ve Uygulama Rehberi

> **Temel Felsefe:** *"Düşüncelerinizi tercüme edebilmek ve yapay zeka ile etkili bir şekilde etkileşim kurabilmek, günümüzde evrensel bir teknik beceridir (universal technical skill)."*

Bu doküman, **"Prompt Engineering: How to Talk to the AIs"** eğitimi kapsamında paylaşılan tüm örnek istemleri (promptları), bu istemlerin arkasındaki mühendislik prensiplerini, çok adımlı yapay zeka ajanı (AI Agent) iş akışlarını, çok modlu (multimodal) kullanım senaryolarını, akademik/pratik kaynakları ve güncel yapay zeka model ekosistemini derinlemesine inceleyen kapsamlı bir başvuru kılavuzudur.

---

## İçindekiler
1. [Temel Prompt Mühendisliği Yapı Taşları ve Anatomisi](#1-temel-prompt-mühendisliği-yapı-taşları-ve-anatomisi)
2. [Yapay Zeka Ajanları (AI Agents): Müşteri Desteği İş Akışı](#2-yapay-zeka-ajanları-ai-agents-müşteri-desteği-iş-akışı)
3. [Çok Modlu (Multimodal) Yapay Zeka Promptları](#3-çok-modlu-multimodal-yapay-zeka-promptları)
4. [Daha Güvenilir ve Kaliteli Sonuçlar İçin İleri Teknikler](#4-daha-güvenilir-ve-kaliteli-sonuçlar-için-ileri-teknikler)
5. [Öğrenmeye Devam Etmek İçin Önerilen Kaynaklar ve Araçlar](#5-öğrenmeye-devam-etmek-için-önerilen-kaynaklar-ve-araçlar)
6. [Yapay Zeka Model Ekosistemi: Hangi Model Ne Zaman Kullanılmalı?](#6-yapay-zeka-model-ekosistemi-hangi-model-ne-zaman-kullanılmalı)
7. [Hızlı Kontrol Listesi (Prompt Tasarım Şablonu)](#7-hızlı-kontrol-listesi-prompt-tasarım-şablonu)

---

## 1. Temel Prompt Mühendisliği Yapı Taşları ve Anatomisi

Etkili bir prompt, rastgele yazılmış bir cümle değil; bağlamın, kısıtlamaların, örneklerin ve çıktı formatının bilinçli olarak bir araya getirildiği yapılandırılmış bir talimattır. Eğitimde incelenen temel prompt türleri ve mühendislik analizleri aşağıdadır:

### 1.1. Metinden Görsel Üretimi (Text-to-Image Generation Prompt)
Görsel üretim modellerinde başarılı sonuç almak için soyut ifadeler yerine **tasarım stili, renk paleti, kompozisyon düzeni, spesifik objeler ve genel atmosfer** net biçimde tanımlanmalıdır.

* **Orijinal Prompt:**
  > *"Generate a clean, flat-design minimalist infographic, rendered in bold orange and slate gray on a clean white background, illustrating a complete marathon pacing and fueling strategy. A continuous horizontal path connects mile markers from a 'START' to a 'FINISH (26.2 miles)' arc. Two parallel rows of clear vector icons are arranged above and below the path: a series of stopwatches showing specific times and pace goals (for example, EASY, CONSERVE, DIG DEEP), along with multiple icons for water cups and energy gels. Include a large final clock showing a sub-four-hour goal achieved message. The overall style is athletic and highly structured."*

* **Türkçe Çevirisi:**
  > *"Temiz beyaz bir arka plan üzerinde koyu turuncu ve arduvaz grisi renklerle işlenmiş, eksiksiz bir maraton tempo (pacing) ve beslenme stratejisini gösteren temiz, düz tasarımlı (flat-design) minimalist bir infografik oluştur. Sürekli bir yatay yol, 'BAŞLANGIÇ'tan 'BİTİŞ (26,2 mil)' yayına kadar mil işaretlerini birbirine bağlar. Yolun üstünde ve altında iki paralel sıra halinde net vektör ikonları dizilmiştir: belirli süreleri ve tempo hedeflerini (örneğin KOLAY, KORU, SONUNA KADAR ZORLA) gösteren bir dizi kronometre ile birlikte su bardakları ve enerji jelleri için çoklu ikonlar. Dört saatin altında hedefe ulaşıldığı mesajını gösteren büyük bir final saati ekle. Genel stil atletik ve oldukça yapılıdır."*

* **Mühendislik Analizi (Neden İşe Yarıyor?):**
  * **Stil ve Tür:** `clean, flat-design minimalist infographic` (Minimalist düz tasarım infografik).
  * **Renk Paleti:** `bold orange and slate gray on a clean white background` (Kontrast ve görsel bütünlük sağlar).
  * **Konu:** `complete marathon pacing and fueling strategy` (İçeriğin ana teması).
  * **Mekansal Düzen (Layout):** `continuous horizontal path`, `two parallel rows above and below` (Modelin objeleri tuvalde nereye yerleştireceğini belirler).
  * **Spesifik Detaylar ve İkonlar:** Kronometreler, su bardakları, enerji jelleri, 4 saat altı final saati.
  * **Genel Atmosfer (Vibe):** `athletic and highly structured`.

---

### 1.2. Sistem Bağlamı ve Talimatlar (System Context and Instructions Prompt)
Modele bir **rol (persona)** ve **davranış tonu (tone of voice)** atamak, üretilecek yanıtın kelime seçimini, perspektifini ve derinliğini doğrudan şekillendirir.

* **Orijinal Prompt:**
  > *"You are an expert tour guide in Barcelona. You are helpful and polite, but also quirky and funny. Give me suggestions about main attractions, restaurants and off-the-beaten-path sights for a three-day visit to the city."*

* **Türkçe Çevirisi:**
  > *"Barselona'da uzman bir tur rehberisin. Yardımsever ve kibarsın ama aynı zamanda kendine has (ilginç/tuhaf) ve eğlencelisin. Şehre yapılacak üç günlük bir ziyaret için ana cazibe merkezleri, restoranlar ve az bilinen (turistik olmayan) yerler hakkında bana önerilerde bulun."*

* **Mühendislik Analizi:**
  * **Kimlik/Rol (Persona):** Barselona'da uzman tur rehberi (Bilgi havuzunu coğrafi ve mesleki olarak odaklar).
  * **Karakter ve Ton:** Yardımsever, kibar, esprili ve kendine has (`quirky and funny`). Sıkıcı bir ansiklopedi dili yerine samimi bir anlatım üretir.
  * **Kapsam ve Kısıt:** 3 günlük süre; ana turistik yerler + restoranlar + az bilinen noktalar (`off-the-beaten-path`).

---

### 1.3. Soru ve Çıktı Kısıtlaması / Formatı (Question and Output Constraint/Format Prompt)
Modelin ne cevap vereceği kadar, cevabı **nasıl sunacağını** sınırlandırmak da okunabilirliği artırır.

* **Orijinal Prompt:**
  > *"What are the top five things you recommend to visit in Barcelona? Write the output using a numbered list"*
* **Türkçe Çevirisi:**
  > *"Barselona'da ziyaret edilmesini önerdiğin en iyi beş yer neresidir? Çıktıyı numaralı bir liste kullanarak yaz."*
* **Mühendislik Analizi:**
  * **Nicelik Kısıtı:** `top five things` (Sadece en önemli 5 öğe ile sınırlandırır, gereksiz uzatmaları önler).
  * **Biçim Kısıtı:** `numbered list` (1'den 5'e kadar numaralandırılmış yapı).

---

### 1.4. Talimatlar ve Girdi Verisi (Instructions and Input Data Prompt)
Genel geçer öneriler yerine kişiselleştirilmiş yanıtlar almak için **talimat (instruction)** ile **kullanıcı verisi/bağlam (input data)** birleştirilir.

* **Orijinal Prompt:**
  > *"Given the following information about me, recommend what to visit in a three-day stay in Barcelona. I am a foodie, enjoy art and music, and love hiking and the outdoors. I prefer to avoid crowds and long lines or overly touristy sites. I prefer authentic and local spots."*
* **Türkçe Çevirisi:**
  > *"Hakkımdaki aşağıdaki bilgileri göz önünde bulundurarak, Barselona'da üç günlük bir konaklamada nereleri ziyaret etmem gerektiğini öner. Ben bir gurcanım (yemek tutkunu), sanat ve müzikten keyif alırım, doğa yürüyüşlerini ve açık havayı severim. Kalabalıklardan, uzun kuyruklardan veya aşırı turistik yerlerden kaçınmayı tercih ederim. Otantik ve yerel mekanları tercih ederim."*
* **Mühendislik Analizi:**
  * **Pozitif Tercihler:** Gastronomi (`foodie`), sanat, müzik, doğa yürüyüşü (`hiking`), otantik ve yerel noktalar.
  * **Negatif Filtreler (Kaçınılacaklar):** Kalabalıklar, uzun kuyruklar, aşırı turistik tuzaklar.

---

### 1.5. Örnekler ve Soru Promptu (Examples and Question / Few-Shot Tercih Yönlendirmesi)
Soyut zevkleri kelimelerle anlatmak zor olduğunda, modele **pozitif ve negatif örnekler** vermek en hızlı hizalanma yöntemidir.

* **Orijinal Prompt:**
  > *"Here are some examples of music I really like: Radiohead, Lana del Rey, and Bon Iver. I do not like Coldplay or Taylor Swift. What other music would you recommend?"*
* **Türkçe Çevirisi:**
  > *"İşte gerçekten sevdiğim müziklerden bazı örnekler: Radiohead, Lana del Rey ve Bon Iver. Coldplay veya Taylor Swift sevmiyorum. Başka hangi müzikleri önerirsin?"*
* **Mühendislik Analizi:**
  * Model, sevilen sanatçıların ortak kesişim kümesini (melankolik, alternatif/indie, atmosferik tınılar) çıkarırken; sevilmeyen sanatçılar (ana akım stadyum rock / pop) üzerinden sınır çizgisini netleştirir.

---

### 1.6. Belirsiz (Vague) vs. Somut (Concrete) Prompt Karşılaştırması

Bir prompt ne kadar belirsizse, yapay zekanın üreteceği yanıt da o kadar sıradan ve tahmin edilemez olur.

| Özellik | Belirsiz Prompt (Vague) | Somut Prompt (Concrete) |
| :--- | :--- | :--- |
| **Metin** | *"Recommend some music I might like."* (Sevebileceğim birkaç müzik öner.) | *"Recommend five indie folk bands similar to Bon Iver or Fleet Foxes. Do not recommend any artists that have had a Top 40 Billboard hit. Format the output as a bulleted list with a one-sentence description of each band's sound."* |
| **Türkçe Çevirisi** | Sevebileceğim müzikler öner. | Bon Iver veya Fleet Foxes benzeri beş indie folk grubu öner. Billboard Top 40 listesinde hit şarkısı olan hiçbir sanatçıyı önerme. Çıktıyı, her grubun müzikal tınısını anlatan tek cümlelik bir açıklamayla madde işaretli liste olarak formatla. |
| **Tür / Referans** | Yok (Tamamen rastgele) | Indie folk / Bon Iver & Fleet Foxes referanslı |
| **Adet Sınırı** | Belirsiz (`some`) | Net (`five bands`) |
| **Negatif Kısıt** | Yok | `No Top 40 Billboard hit` (Ana akım olmayanları filtreler) |
| **Çıktı Formatı** | Serbest metin | Madde işaretli liste + grup başına 1 cümlelik ses tanımı |

---

## 2. Yapay Zeka Ajanları (AI Agents): Müşteri Desteği İş Akışı

Kurumsal bir yapay zeka sisteminde (örneğin bir havayolu müşteri destek ajanında) tek bir basit prompt kullanmak hatalara (halüsinasyonlara) yol açabilir. Eğitimde, güvenilir bir ajan mimarisinin **4 aşamalı evrimi** bir vaka analizi üzerinden gösterilmektedir:

### Senaryo Verileri:
* **Şirket Politikası:** 3 saati aşan uçuş gecikmeleri için 100$ öde (*hava durumu kaynaklı gecikmeler hariç*). Kayıp bagaj için günlük 50$ öde.
* **Müşteri E-postası:** *"Uçuşum şiddetli bir fırtına nedeniyle dört saat rötar yaptı ve bagajım iki gün boyunca kayboldu."*

---

### Adım 1: Retrieval-Augmented Generation (RAG) — Bağlam ve Temel Çizgi (The Context and Baseline)
Modelin kendi eğitim verisinden uydurma kurallar çıkarmasını önlemek için ilgili şirket politikası doğrudan prompt içine enjekte edilir.

* **Orijinal Prompt:**
  > *"Policy: Pay $100 for flight delays over three hours (except weather related). Pay $50 per day for lost bags.*
  > *Customer email: 'My flight was delayed four hours due to a severe storm, and my bag was lost for two days.'*
  > *Draft a reply."*
* **Analiz ve Risk:** Model politikayı görür ancak doğrudan yanıt yazmaya başladığı için ("Draft a reply"), 4 saatlik gecikmenin "fırtına" (hava durumu istisnası) kaynaklı olduğunu gözden kaçırıp yanlışlıkla 100$ + 100$ = 200$ tazminat sözü verebilir.

---

### Adım 2: Düşünce Zinciri Ekleme (Chain of Thought - CoT) — Muhakeme (The Reasoning)
Modeli nihai çıktıyı üretmeden önce **adım adım düşünmeye ve hesaplama yapmaya** zorlamak, mantıksal hataları büyük oranda ortadan kaldırır.

* **Orijinal Prompt:**
  > *"Policy: Pay $100 for flight delays over three hours (except weather-related). Pay $50 per day for lost bags.*
  > *Customer email: 'My flight was delayed four hours due to a severe storm, and my bag was lost for two days.'*
  > *Draft a reply but before drafting the email, think step by step to calculate the total compensation owed based strictly on the policy."*
* **Türkçe Çevirisi:**
  > *"...Bir yanıt taslağı hazırla ancak e-postayı yazmadan önce, kesin olarak politikaya dayalı toplam tazminatı hesaplamak için adım adım düşün."*
* **Mühendislik Analizi:**
  Model önce şu içsel muhakemeyi yapar:
  1. *Uçuş gecikmesi:* 4 saat (>3 saat koşulu sağlanıyor). Ancak sebep "şiddetli fırtına" (hava durumu istisnası var). Tazminat = **0$**.
  2. *Kayıp bagaj:* 2 gün sürdü. Günlük 50$ * 2 gün = **100$**.
  3. *Toplam Ödenecek:* **100$**.
  Bu muhakeme tamamlandıktan sonra yazılan e-posta hatasız olur.

---

### Adım 3: Öz-Denetim (Self-Check / Reflection) — Doğrulama (The Verification)
Modelin ürettiği ilk taslağı kendi kendisine denetlemesi ve hem kural doğruluğunu hem de iletişim tonunu iyileştirmesi aşamasıdır.

* **Orijinal Prompt:**
  > *"Review your drafted email. Are you absolutely sure you applied the weather exception correctly? Also, review the tone. Make it warmer and more empathetic before finalizing."*
* **Türkçe Çevirisi:**
  > *"Hazırladığın e-posta taslağını gözden geçir. Hava durumu istisnasını doğru uyguladığından tamamen emin misin? Ayrıca tonu gözden geçir. Son haline getirmeden önce daha sıcak ve daha empatik hale getir."*
* **Mühendislik Analizi:**
  * İkinci bir kontrol katmanı ekleyerek olası politika ihlallerini yakalar.
  * Müşteriye "Fırtına yüzünden para vermiyoruz" gibi soğuk bir ifade yerine, yaşanan aksaklıktan dolayı üzüntü belirten empatik bir müşteri ilişkileri dili kazandırır.

---

### Adım 4: Hakem Olarak LLM (LLM-as-a-Judge) — Değerlendirme (The Evaluation)
Üretilen yanıt müşteriye gönderilmeden önce, farklı bir sistem promptuyla yapılandırılmış bağımsız bir "Kalite Kontrol (QA) Modeli" tarafından puanlanır.

* **Orijinal Prompt:**
  > *“You are a Customer Service QA Manager. Evaluate this drafted response against the Airline Policy. Score it from 1 to 5 on Policy Accuracy and Empathetic Tone. If it scores below a 4, flag it for human review."*
* **Türkçe Çevirisi:**
  > *"Sen bir Müşteri Hizmetleri Kalite Güvence (QA) Yöneticisisin. Bu taslak yanıtı Havayolu Politikasına göre değerlendir. Politika Doğruluğu ve Empatik Ton açısından 1 ile 5 arasında puanla. Eğer 4'ün altında puan alırsa, insan incelemesi (human review) için işaretle."*
* **Mühendislik Analizi:**
  * **Otomatik Kalite Kapısı (Quality Gate):** Belirli bir eşik değerin (`< 4`) altındaki çıktılar otomatik olarak insan temsilciye (`human-in-the-loop`) yönlendirilir. Bu, kurumsal yapay zeka uygulamalarında güvenlik ve kalite standardı sağlar.

---

## 3. Çok Modlu (Multimodal) Yapay Zeka Promptları

Modern yapay zeka modelleri yalnızca metinlerle değil; **görüntü, ses ve grafiklerle** de etkileşime girebilir. Eğitimde vurgulanan 4 temel çok modlu kullanım senaryosu:

1. **Fiziksel Arıza Teşhisi ve Onarım (Fotoğraf + Metin):**
   * **Eylem:** Bozuk bisikletinizin bir fotoğrafını yükleyin.
   * **Prompt:** *"What is wrong here, and what tools do I need to fix it?"* (Burada sorun nedir ve bunu düzeltmek için hangi aletlere ihtiyacım var?)
2. **Teknik Hata Ayıklama / Debugging (Ekran Görüntüsü + Metin):**
   * **Eylem:** Bir hata mesajının ekran görüntüsünü (screenshot) yükleyin.
   * **Prompt:** *"What does this error mean, and what should I try next?"* (Bu hata ne anlama geliyor ve bir sonraki adımda ne denemeliyim?)
3. **Veri Analizi ve İçgörü Çıkarımı (Grafik Görseli + Metin):**
   * **Eylem:** Bir rapordan alınan grafiği yükleyin.
   * **Prompt:** *"What are the three most important trends in this chart?"* (Bu grafikteki en önemli üç trend nedir?)
4. **Toplantı ve Ses Kaydı Analizi (Ses Dosyası + Metin):**
   * **Eylem:** Bir toplantı ses kaydını (audio file) yükleyin.
   * **Prompt:** *"Who agreed to take on the marketing deliverables?"* (Pazarlama teslimatlarını/görevlerini üstlenmeyi kim kabul etti?)

---

## 4. Daha Güvenilir ve Kaliteli Sonuçlar İçin İleri Teknikler

Yapay zeka sistemlerinden daha tutarlı, öngörülebilir ve başka yazılımlarla entegre edilebilir çıktılar almak için iki altın kural öne çıkmaktadır:

### 4.1. Çıktı Formatını Açıkça Belirtin (Specify the Output Format)
Modeli serbest bırakmak yerine ihtiyacınız olan veri yapısını dikte edin:

* **Yönetici Özeti Formatı (Madde İşaretleri + Tek Cümlelik Ana Çıkarım):**
  > *"Summarize this article in five bullet points. Then include a one-sentence takeaway at the end."*
  > *(Bu makaleyi beş madde işaretiyle özetle. Ardından sonuna tek cümlelik bir ana çıkarım ekle.)*

* **Yapılandırılmış Tablo Formatı (Bilgi Çıkarımı / Information Extraction):**
  > *"Identify AI models in the article. Extract their names, year, lab/company that developed them, and key novel capability/functionality. Return the answer as a table."*
  > *(Makaledeki yapay zeka modellerini belirle. İsimlerini, yıllarını, onları geliştiren laboratuvarı/şirketi ve temel yenilikçi yeteneklerini/işlevlerini çıkar. Yanıtı bir tablo olarak döndür.)*

* **Yazılım / API Entegrasyonu İçin Salt JSON Formatı:**
  > *"Extract the model names and years from the article. Respond only in valid JSON."*
  > *(Makaleden model isimlerini ve yıllarını çıkar. Yalnızca geçerli bir JSON ile yanıt ver.)*
  * *Not:* `"Respond only in valid JSON"` ifadesi, modelin JSON bloğu öncesine veya sonrasına *"İşte istediğiniz JSON verisi:"* gibi sohbet metinleri eklemesini engelleyerek kod tarafında `JSON.parse()` hatalarını önler.

### 4.2. Modelin Açıklayıcı Sorular Sormasını Sağlayın (Get the Model to Ask Clarifying Questions)
Her zaman mükemmel promptu tek seferde yazamayabilirsiniz. **Tersine Etkileşim (Flipped Interaction)** tekniği ile modelin eksik bilgileri sizden toplamasını sağlayabilirsiniz.

* **Orijinal Prompt:**
  > *"Give me recommendations for what to see during a weekend in Barcelona.*
  > *But first, ask me three clarifying questions to better understand my preferences. Ask one question at a time."*
* **Türkçe Çevirisi:**
  > *"Barselona'da bir hafta sonu boyunca görülecek yerler için bana önerilerde bulun. Ama önce, tercihlerimi daha iyi anlamak için bana üç açıklayıcı soru sor. Her seferinde bir soru sor."*
* **Mühendislik Analizi:**
  * `"Ask one question at a time"` (Her seferinde tek bir soru sor) kısıtı kritik öneme sahiptir; kullanıcının uzun bir soru listesiyle bunalmasını önler ve gerçek bir danışmanlık diyaloğu başlatır.

---

## 5. Öğrenmeye Devam Etmek İçin Önerilen Kaynaklar ve Araçlar

Eğitimde, prompt mühendisliğinden tam kapsamlı yapay zeka mühendisliğine geçiş için önerilen temel kaynaklar şunlardır:

| Kategori | Kaynak / Araç Adı | Açıklama ve Kullanım Amacı |
| :--- | :--- | :--- |
| **Uygulamalı Pratik** | **Anthropic’s Prompt Engineering Interactive Tutorial** | Promptlama tekniklerini adım adım anlatan ve örneklerle interaktif olarak pratik yapmayı sağlayan başlangıç için mükemmel bir rehber. |
| **Resmi En İyi Uygulamalar** | **OpenAI’s Prompt Engineering Guide** | Net talimatlar yazma, referans metin sağlama, karmaşık görevleri alt parçalara bölme, araç (tool) kullanımı ve değişiklikleri sistematik test etme üzerine pratik stratejiler. |
| **Akademik Derinlik** | **“Prompt Design and Engineering: Introduction and Advanced Methods”** | Eğitimcinin kaleme aldığı akademik makale. Chain-of-Thought (CoT), öz-yansıtma (reflection), ajanlar (agents) ve prompt mühendisliği araçlarının kapsamlı incelemesi. |
| **Ajan Mimarisi Temelleri** | **ReAct Makalesi (Reasoning and Acting)** | Dil modellerinin muhakeme (reasoning) ile eylemi (acting) birleştirerek dış araçları (external tools) veya ortamları kullanmasını tanıtan kurucu akademik makale. |
| **Uygulama Geliştirme Çatıları** | **LangChain & LangGraph** | **LangChain:** LLM uygulamaları için ortak yapı taşları sunar.<br>**LangGraph:** Durum bilgisi olan (stateful), çok adımlı ve döngüsel ajan iş akışları (agent workflows) oluşturmaya odaklanır. |
| **Programatik Optimizasyon** | **DSPy** | Promptları elle yazılan metinler olmaktan çıkarıp, otomatik ve algoritmik olarak optimize edilebilen programatik bileşenler olarak ele alan ileri düzey çatı. |

---

## 6. Yapay Zeka Model Ekosistemi: Hangi Model Ne Zaman Kullanılmalı?

Her görev için en büyük veya en pahalı modeli kullanmak doğru değildir. İş akışınıza (workflow) en uygun modeli seçmek için modeller 5 ana kategoride sınıflandırılmıştır:

### 6.1. Hızlı Modeller: İcraatçılar (Fast Models: The Doers)
Düşük gecikme süresi (low latency), yüksek hız ve düşük maliyet gerektiren yüksek hacimli günlük görevler (özetleme, sınıflandırma, basit veri çıkarımı) için idealdir.
* **Google:** Gemini Flash
* **Anthropic:** Claude Haiku
* **OpenAI:** GPT Mini

### 6.2. Küçük Açık Ağırlıklı Modeller: Yerel Kahramanlar (Small Open-Weight Models: The Local Heroes)
Kendi donanımınızda (on-premise / local) çalıştırılabilen, veri gizliliğinin kritik olduğu veya internet bağlantısı olmadan özelleştirilerek (fine-tuning) kullanılabilen modellerdir.
* **Gemma** (Google)
* **DeepSeek**
* **Llama** (Meta)
* **Mistral**
* **Qwen** (Alibaba)

### 6.3. Düşünen Modeller: Muhakemeciler (Thinking Models: The Reasoners)
Yanıt vermeden önce içsel olarak uzun düşünce zincirleri kuran; karmaşık matematik, ileri düzey kodlama, bilimsel analiz ve çok adımlı stratejik planlama görevlerinde uzmanlaşmış modellerdir.
* **OpenAI:** ChatGPT o3 ve ChatGPT-5
* **Google:** Gemini Pro Thinking
* **Anthropic:** Claude Opus, Mythos
* **DeepSeek:** DeepSeek R2

### 6.4. Metinden Görsele Modeller (Text-to-Image Models)
İnfografik, konsept tasarım, illüstrasyon ve fotogerçekçi görsel üretim araçları:
* **Midjourney**
* **FLUX**
* **OpenAI Image** *(Eski adıyla DALL-E)*
* **Google Nano Banana** *(Diğer adıyla Gemini Image)*

### 6.5. Metinden Videoya Modeller (Text-to-Video Models)
Metin komutlarından veya referans görsellerden sinematik video kesitleri ve animasyonlar üreten modeller:
* **Google:** Veo
* **OpenAI:** Sora
* **Runway:** Gen-3 Alpha

---

## 7. Hızlı Kontrol Listesi (Prompt Tasarım Şablonu)

Kendi promptlarınızı yazarken aşağıdaki kontrol listesini kullanarak mühendislik kalitesini artırabilirsiniz:

1. **Rol ve Ton (Persona & Tone):** Model kim olmalı ve nasıl bir üslupla konuşmalı? *(Örn: Empatik bir müşteri temsilcisi, esprili bir rehber, QA yöneticisi)*
2. **Bağlam ve Girdi Verisi (Context & Input Data):** Modelin karar verirken dayanacağı kurallar, politikalar veya kişisel tercihler neler? *(RAG verisi, kullanıcı profili)*
3. **Somut Görev ve Kısıtlamalar (Concrete Task & Constraints):** Kaç adet öneri istiyorsunuz? Nelerden kesinlikle kaçınılmalı? *(Negatif promptlar)*
4. **Muhakeme Beklentisi (Reasoning):** Doğrudan cevaba mı atlamalı yoksa önce adım adım düşünmeli mi? *("Think step by step")*
5. **Çıktı Formatı (Output Format):** Yanıt nasıl sunulmalı? *(Numaralı liste, Markdown tablosu, salt JSON, tek cümlelik özet)*
6. **Kalite Kontrol ve Etkileşim (Verification & Clarification):** Model eksik bilgi varsa önce soru mu sormalı, yoksa çıktısını ürettikten sonra kendi kendini mi denetlemeli?
