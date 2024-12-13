# Try-Catch-Finally ve Mantıksal Hatalar

## Giriş

Bu belge, **Try-Catch-Finally** yapısını ve mantıksal hataları detaylı bir şekilde ele alır. Programlama yaparken hata yakalama ve hata yönetimi kritik bir konudur. Bu belge ile şu başlıkların üzerinden geçeceğiz:

1. Try-Catch-Finally nedir ve neden kullanılır?
2. Mantıksal hatalar nedir, neden tehlikelidir?
3. Örneklerle anlatım.

---

## Try-Catch-Finally Nedir?

### Try

**Try** bloğu, hata oluşma ihtimali olan kodların yazıldığı yerdir. Hata meydana geldiğinde bu hata yakalanır ve programın doğrudan çökmesi önlenir.

```csharp
try
{
    int sayi = Convert.ToInt32("abc"); // Geçersiz bir dönüşüm, hata oluşturur.
}
```

### Catch

**Catch** bloğu, **try** içinde meydana gelen hataları ele alır. Farklı hata türlerini yakalamak için birden fazla catch bloğu kullanabilirsiniz.

```csharp
catch (FormatException ex)
{
    Console.WriteLine($"Format hatası: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Beklenmedik bir hata: {ex.Message}");
}
```

### Finally

**Finally** bloğu, bir hata oluşsa da oluşmasa da her zaman çalışacak olan kodları barındırır. Genellikle kaynak temizleme gibi işlemler için kullanılır.

```csharp
finally
{
    Console.WriteLine("Kod tamamlandı, kaynaklar serbest bırakıldı.");
}
```

### Tam Bir Try-Catch-Finally Yapısı

```csharp
try
{
    Console.WriteLine("Bir sayı giriniz:");
    int sayi = Convert.ToInt32(Console.ReadLine());
    Console.WriteLine($"Girdiğiniz sayı: {sayi}");
}
catch (FormatException ex)
{
    Console.WriteLine("Lütfen geçerli bir sayı giriniz.");
}
catch (Exception ex)
{
    Console.WriteLine($"Beklenmeyen bir hata oluştu: {ex.Message}");
}
finally
{
    Console.WriteLine("Program sonlandı.");
}
```

---

## Mantıksal Hatalar Nedir?

Mantıksal hatalar (Logical Errors), kodun yazımında bir hata olmamasına rağmen programın beklenen çıktıyı vermediği durumları ifade eder. Bu hatalar, genellikle algoritma veya iş mantığındaki sorunlardan kaynaklanır.

### Mantıksal Hataya Örnek

Bir uygulama, girilen iki sayıyı toplamak yerine çarpmış olsun:

```csharp
int sayi1 = 5;
int sayi2 = 10;

// Toplama yapılması gerekirken çarpma yapılıyor
int sonuc = sayi1 * sayi2;

Console.WriteLine($"Sonuç: {sonuc}"); // Beklenen: 15, Gerçek: 50
```

### Mantıksal Hataları Bulma Yöntemleri

1. **Debugging:** Kodunuzu adım adım izleyerek hatayı tespit edin.
2. **Unit Test:** Kodunuzun her bir bölümünü test eden birimler yazın.
3. **Kod Gözden Geçirme:** Kodunuzu ekip arkadaşlarınıza inceletin.

---

## Try-Catch-Finally ve Mantıksal Hatalar Arasındaki Fark

- **Try-Catch-Finally**, **sistemsel** hataları yakalar ve bu hataları ele alır.
- **Mantıksal hatalar**, programcının algoritma veya mantık yanlışından kaynaklanır ve genellikle hata mesajı oluşturmaz. Bu nedenle, mantıksal hataları yakalamak için özel çabalar gerekir.

---

## Neden Önemlidir?

1. **Try-Catch-Finally:**

   - Programınızın beklenmedik çökmelerini önler.
   - Kullanıcı dostu hata mesajları oluşturur.
   - Kaynak temizleme gibi kritik işlemleri garantiler.

2. **Mantıksal Hatalar:**
   - Uygulamanın doğru çalışmasını sağlar.
   - Kullanıcı memnuniyetini arttırır.
   - Sistemsel hataları önceden önler.

---

## Sık Karşılaşılan Hatalar ve Çözümler

### NullReferenceException

Bir nesneye **null** değeri varken erişim yapılmaya çalışıldığında meydana gelir.

**Çözüm:** Nesne null kontrolü yapılmalıdır.

```csharp
string metin = null;

if (metin != null)
{
    Console.WriteLine(metin.Length);
}
else
{
    Console.WriteLine("Metin null değerine sahip.");
}
```

### Mantıksal Hataları Düzeltme

Yanlış algoritmanızı yeniden düzenleyin ve unit test kullanın.

```csharp
// Yanlış kod
int sayi1 = 5;
int sayi2 = 10;
int sonuc = sayi1 * sayi2; // Çarpma yerine toplama olmali

// Doğru kod
sonuc = sayi1 + sayi2;
```

---

## Sonuç

Bu belgede, **Try-Catch-Finally** yapısının ve mantıksal hataların ne olduğunu öğrendiniz. Programlarınızı daha sağlam ve hataya dayanıklı hale getirmek için bu iki konuya hakim olmanız çok önemlidir. Her zaman kodunuzu test edin, şüpheli kodlar için hata yakalama mekanizmaları kurun ve mantıksal hataları minimize etmeye çalışın.
