# Step 5: Feature Engineering ✨

* Create at least **two new features** that could help predict income.
* Think about combinations, transformations, or new groupings of existing variables.
* Explain your reasoning: why might these new features help?


This is Step 5: Feature Engineering, where we use our domain knowledge of income data to create new variables that will boost the predictive power of the model.

<img width="911" height="318" alt="image" src="https://github.com/user-attachments/assets/3ff6b873-fb1d-4f73-b91a-026b8e265dc5" />

<img width="878" height="462" alt="image" src="https://github.com/user-attachments/assets/a4186495-6a97-493f-a260-429d6eef8354" />

<img width="598" height="293" alt="image" src="https://github.com/user-attachments/assets/d0078d24-e75a-44f1-92ff-1e70ef8e4de2" />




---
---
## Turkish:

## 🛠️ Feature Engineering Uygulamasına İlişkin Profesyonel Yorum

Bu analiz, Feature Engineering sürecini üç anahtar bakış açısıyla yorumlamaktadır:

1. Stratejik Yaklaşım (Veri Sinyalini Çıkarma)

2. Uygulama Tutarlılığı (Kodlama ve Temizlik)

3. Model Etkisi (Yeni Özelliklerin Potansiyeli)

### 1. Stratejik Yorum: Sinyal Güçlendirme (Signal Augmentation) ✨

Uygulanan adımlar, veri setindeki zayıf veya karmaşık sinyalleri başarıyla güçlendirmiş ve modelin yorumlamasını basitleştirmiştir:

* **Capital Interaction (`Has_Capital_Activity`)**: **`capital-gain`** ve **`capital-loss`** gibi yüksek oranda sıfır içeren (skewed) değişkenler, mutlak değerleri yerine **mevcudiyetleri** üzerine odaklanılarak ikili (**binary**) bir gösterge oluşturulmuştur. Bu, modelin sıfırdan farklı olan nadir gözlemleri daha net ayırt etmesini sağlar ve gürültüyü azaltır.
* **Work Intensity (`Work_Intensity`)**: Sürekli değişken olan **`hours-per-week`**, uzmanlık bilgisi kullanılarak (**PartTime, FullTime, Overtime**) ayrık, anlamlı kategorilere dönüştürülmüştür (**Binning**). Bu, Lojistik Regresyon'un **doğrusallık** varsayımı için daha iyi bir sinyal sağlar.

### 2. Uygulama Yorumu: Kodlama ve Tutarlılık 🧪

Uygulanan kodlama yöntemleri **production (üretim) ortamı** düşünülerek seçilmiştir:

* **Doğru Kodlama Yöntemi:** Yeni oluşturulan `Work_Intensity` kategorik özelliği, rastgele sayı ataması yerine **`OneHotEncoder`** kullanılarak kodlanmıştır. Bu, kategoriler arasında yanlış bir sıra ilişkisi kurulmasını engeller.
* **Kod Tutarlılığı:** Tüm veri manipülasyonları (`pd.cut`, `np.where`) Pandas'ın güvenceli atama metotları olan **`.loc`** ile yapılmıştır. Bu, **`SettingWithCopyWarning`** gibi hataları önleyerek veri bütünlüğünü sağlamaktadır.
* **Temizlik:** İşlenen veya yedek olarak kullanılan orijinal metin/sayısal sütunların (örneğin, orijinal `Work_Intensity` metin sütunu) final DataFrame'den **`drop`** edilmesi, modelin sadece en temiz ve en sinyalli özelliklerle eğitilmesini garanti etmiştir.

### 3. Sonuç ve Model Etkisi (Model Impact) 🚀

Bu Feature Engineering aşaması, ham verinin potansiyelini maksimize etmiştir:

> "Bu süreç, modelin Titanic veri setinde **Sex** ve **Pclass** gibi güçlü demografik özelliklerle birlikte, **Has_Capital_Activity** ve **Work_Intensity** gibi yapılandırılmış ekonomik sinyalleri kullanmasını sağlayarak tahmin gücünü önemli ölçüde artıracaktır."
