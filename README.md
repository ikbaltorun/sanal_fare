# Sanal Fare Kontrolcüsü (Virtual Mouse Controller) 🖱️🤖

Bu proje, bilgisayar kamerasından alınan görüntüleri işleyerek, fiziksel bir fareye ihtiyaç duymadan ekrandaki imleci el hareketleriyle yönetmenizi sağlayan gerçek zamanlı bir "Computer Vision" (Görüntü İşleme) uygulamasıdır.

## 📌 Proje Hakkında
Sistem, Google'ın yeni nesil **MediaPipe Tasks API** mimarisini kullanarak el eklem noktalarını (landmarks) milisaniyelik gecikmelerle tespit eder. İşaret parmağının ucu (Landmark 8) ekranın en/boy oranına göre matematiksel olarak haritalandırılır ve `PyAutoGUI` kütüphanesi ile işletim sistemine fare komutu olarak iletilir.

## 🚀 Özellikler
* **Gerçek Zamanlı İmleç Kontrolü:** İşaret parmağınızı havada hareket ettirerek bilgisayarınızın imlecini gecikmesiz olarak yönlendirebilirsiniz.
* **Dokunmatik Olmayan Tıklama (Click):** İşaret parmağı (Landmark 8) ile başparmak (Landmark 4) uçları arasındaki Öklid mesafesi hesaplanır. İki parmak birbirine temas ettiğinde (cımbız hareketi) sistem bunu algılar ve sol tıklama (Left Click) işlemini gerçekleştirir.
* **Otomatik Model Yükleme:** MediaPipe'ın `hand_landmarker.task` yapay zeka modeli, proje ilk çalıştırıldığında cihazda yoksa otomatik olarak Google sunucularından indirilir.

## 🛠️ Kullanılan Teknolojiler
* **Python 3.x**
* **OpenCV (`cv2`):** Görüntü yakalama, çerçeve (frame) işleme ve ekrana çizim işlemleri.
* **MediaPipe (`tasks.python.vision`):** İleri seviye el iskeleti (Hand Tracking) tespiti ve analizi.
* **PyAutoGUI:** İşletim sistemi seviyesinde fare kontrolü ve otomasyon.
* **Math:** Eklemler arası mesafe ve ekran koordinat oranı hesaplamaları.

## ⚙️ Kurulum ve Çalıştırma

Projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyebilirsiniz:

1. Projeyi bilgisayarınıza klonlayın:
   git clone [https://github.com/ikbaltorun/sanal_fare.git]((https://github.com/ikbaltorun/sanal_fare))
   
2. Gerekli kütüphaneleri sanal ortamınıza (venv) kurun:
   pip install opencv-python mediapipe pyautogui

3. Python dosyasını çalıştırın:
   python sanal_fare.py

Not: İlk çalıştırmada yapay zeka modeli otomatik olarak indirileceği için uygulamanın açılması 10-15 saniye sürebilir. Çıkış yapmak için kamera penceresi aktifken klavyeden q tuşuna basmanız yeterlidir.
