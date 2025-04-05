Tabii, işte projenizin detaylı açıklamasını ve neler yaptığına dair açıklamalar:

---

# **Proje Adı: Modbus Gaz Sensörü ve Kalibrasyon Yönetim Sistemi**

## **Proje Hakkında**

Bu proje, bir Modbus tabanlı gaz sensörü cihazının verilerini okuma, yönetme ve kalibrasyon işlemleri gerçekleştiren bir otomasyon sistemidir. Sistem, cihazlar arasındaki veri iletişimini sağlamak için Modbus protokolünü kullanır ve tüm bu işlemler Node-RED platformunda yapılandırılmıştır. Kullanıcılar, bir web arayüzü üzerinden cihazların durumunu izleyebilir ve çeşitli ayarları değiştirebilir.

Proje, özellikle endüstriyel otomasyon ve sensör tabanlı veri izleme sistemlerine yönelik olarak tasarlanmıştır. Bu, özellikle gaz tespiti ve alarm sistemleri gibi kritik uygulamalarda kullanılabilir. Cihazların kalibrasyonu, parametre ayarları ve alarm yönü gibi kontrollerin yönetilmesi sağlanır.

## **Kullanılan Teknolojiler**
- **Node-RED:** Akış tabanlı bir programlama platformudur. Cihazlarla iletişimi, veri işlemleri ve kullanıcı etkileşimlerini yönetir.
- **Modbus Protokolü:** Endüstriyel cihazlarla veri iletimi için kullanılan bir protokoldür. Bu proje Modbus RTU üzerinden cihazlara veri okuma ve yazma işlemleri yapar.
- **JavaScript ve Node.js:** Node-RED içindeki işlevlerin (function node) yazılmasında JavaScript kullanılır. Ayrıca, COM portlarını listelemek için `serialport` kütüphanesi kullanılır.
- **UI Bileşenleri (Dropdown, Button, Template):** Kullanıcı arayüzü için Node-RED'in dahili UI bileşenleri kullanılarak cihaz parametreleri üzerinde etkileşim sağlanır.

## **Projenin Temel Özellikleri**

### **1. Modbus ile Veri Okuma ve Yazma**
Proje, cihazlar arasında veri okuma ve yazma işlemleri için **Modbus** protokolünü kullanır. Modbus RTU (Remote Terminal Unit) protokolü, endüstriyel cihazlar arasında veri iletimi için yaygın olarak kullanılır ve cihazlar arasındaki haberleşmeyi sağlar. Bu sayede, gaz sensörü cihazlarından sıcaklık, gaz seviyesi, alarm durumu gibi veriler okunabilirken, aynı zamanda kalibrasyon değerleri de yazılabilir.

#### **Özellikler:**
- **Veri Okuma:** Modbus üzerinden sensörden sıcaklık, gaz seviyeleri gibi veriler okunur.
- **Veri Yazma:** Kullanıcıların web arayüzü üzerinden seçtiği kalibrasyon değerleri veya alarm yönü gibi parametreler sensöre yazılır.

### **2. Kullanıcı Arayüzü (UI) ile Etkileşim**
Projede, kullanıcıların cihazlarla etkileşime girmesini sağlamak için **Node-RED'in UI bileşenleri** kullanılmıştır. Bu bileşenler aracılığıyla kullanıcılar, cihazın durumunu izleyebilir, kalibrasyon değerlerini değiştirebilir ve alarm yönü gibi ayarları kontrol edebilir.

#### **UI Bileşenleri:**
- **Dropdown (Aşağı/Yukarı Alarm Yönü Seçimi):** Kullanıcı, alarmın yönünü seçebilir. Bu seçim Modbus cihazına iletilir ve cihazın alarm yönü değiştirilir.
- **Formlar (Kalibrasyon ve Gaz Seviye Ayarları):** Kullanıcılar, gaz sensörlerinin kalibrasyon seviyelerini değiştirebilir veya gaz seviyesini ayarlayabilir.
- **Butonlar (Kalibrasyon Sıfırlama):** Kullanıcılar, cihazın kalibrasyon ayarlarını sıfırlamak için butona tıklayabilir.

### **3. COM Portları ile İletişim**
Proje, gaz sensörü cihazlarına **COM portları** üzerinden bağlanarak veri iletişimi kurar. Kullanıcılar, mevcut COM portlarından birini seçerek sensör cihazına bağlanabilir. Bu işlem **serialport** kütüphanesiyle gerçekleştirilir ve COM portları listeleme işlemi yapılır.

#### **COM Port Seçimi:**
- **COM Portları Listeleme:** Sistem, bilgisayarınızdaki mevcut COM portlarını listeler ve kullanıcıların uygun portu seçmesine olanak tanır.
- **Seri Port Bağlantısı:** Seçilen COM portu üzerinden cihazla iletişim başlatılır.

### **4. Kalibrasyon İşlemleri**
Gaz sensörlerinin doğru çalışabilmesi için **kalibrasyon işlemleri** oldukça önemlidir. Proje, gaz sensörlerinin kalibrasyon seviyelerini okuma ve değiştirme işlemlerini sağlar. Bu, sensörlerin doğru veri sağlaması için gereklidir.

#### **Kalibrasyon Özellikleri:**
- **Kalibrasyon Seviye Ayarları:** Kullanıcılar, gaz sensörlerinin kalibrasyon seviyelerini değiştirebilir.
- **Fabrika Ayarlarına Dönme:** Kullanıcılar, cihazın kalibrasyon ayarlarını sıfırlayarak fabrika ayarlarına dönebilir.

### **5. Veri Formatı ve Ölçeklendirme**
Gaz sensörleri, okunan veriyi belirli bir birimde (örneğin: %VOL, ppm, %LEL) sunar. Bu verilerin doğru şekilde işlenmesi ve kullanıcılara doğru formatta sunulması gereklidir. Proje, verileri doğru şekilde formatlar ve birim dönüşümü yapar.

#### **Veri Dönüşümü ve Ölçeklendirme:**
- **Veri Okuma:** Okunan veriler, önce Modbus cihazından alınır ve uygun birimlere dönüştürülür.
- **Birim Seçimi:** Kullanıcılar, verilerin hangi birimde görüntüleneceğini seçebilir. Bu seçim, verinin ekranda doğru bir şekilde gösterilmesini sağlar.
- **FullScale Hesaplaması:** Gaz sensörlerinin full scale (tam ölçek) değerleri hesaplanır ve bu değere göre gaz seviyeleri ölçülür.

### **6. Debugging ve Hata Yönetimi**
Proje, veri okuma ve yazma işlemleri sırasında olabilecek hataları **debugging** yaparak izler. Bu sayede sistemin doğru çalışıp çalışmadığı takip edilebilir.

#### **Debugging Özellikleri:**
- **Veri Gösterimi:** Okunan veriler ve yapılan yazma işlemleri, sistemin düzgün çalışıp çalışmadığını kontrol etmek için debug mesajları olarak kaydedilir.
- **Hata Yönetimi:** Hatalı işlemler veya yanlış girişler hakkında uyarılar gösterilir.

---

## **Proje Akışı**

### **1. Veri Okuma Akışı**
1. **Modbus Cihazlarından Veri Okuma:** Proje, cihazlardan belirli veri noktalarını okur (örneğin gaz seviyesi, sıcaklık vb.). Bu veriler Modbus protokolü ile cihazdan alınır.
2. **Veri Formatlama:** Okunan veriler, kullanıcı arayüzünde gösterilebilmek için uygun formatta işlenir. Bu işlemde birim dönüşümü de yapılır.
3. **Veri Gösterimi:** Kullanıcılar, okunan veriyi UI üzerinden izler.

### **2. Veri Yazma Akışı**
1. **Kullanıcı Seçimleri:** Kullanıcı, web arayüzü üzerinden kalibrasyon değerlerini veya alarm yönünü seçer.
2. **Modbus Cihazına Yazma:** Kullanıcı seçimine göre yazma işlemi yapılır ve değerler Modbus cihazına iletilir.
3. **Geri Bildirim:** Yazma işlemi sonrası, cihazın başarılı bir şekilde güncellendiğine dair kullanıcıya geri bildirim verilir.

---

## **Projenin Kullanıcıya Sağladığı Faydalar**

1. **Veri İzleme:** Kullanıcılar, gaz sensörlerinin çalışmasını ve güncel verilerini sürekli olarak izleyebilir.
2. **Kalibrasyon Yönetimi:** Sensörlerin doğru çalışabilmesi için gerekli kalibrasyon işlemleri, kullanıcılar tarafından kolayca yönetilebilir.
3. **Hata Tespiti:** Sistem, sensörlerle ilgili olası hataları tespit eder ve kullanıcıyı uyarır.
4. **Kolay Etkileşim:** Kullanıcı arayüzü, kullanıcıların hızlıca seçim yapmasına ve işlemleri gerçekleştirmesine olanak tanır.

---

## **Sonuç**

Bu proje, gaz sensörü cihazlarının yönetimi, izlenmesi ve kalibrasyon işlemlerini kolaylaştıran bir çözüm sunmaktadır. Kullanıcılar, cihazlarla etkileşimde bulunarak veri okuma, yazma ve kalibrasyon gibi işlemleri rahatça gerçekleştirebilir. Proje, endüstriyel otomasyon ve sensör yönetimi alanlarında faydalı bir araç olarak kullanılabilir.

---

Bu açıklama, projenizin amacını, işlevlerini ve özelliklerini kullanıcıya en iyi şekilde iletmeyi hedefler. Projeyi geliştiren bir kişi veya ekip için bu tür detaylı bir açıklama, projenin kullanım amacını net bir şekilde ifade etmeye yardımcı olur.
