# 🔐 Kioptrix Level 1 - Sızma Testi (Penetration Test) Raporu

Bu proje, VulnHub üzerinde yayınlanan ve bilinen zafiyetleri barındıran **Kioptrix Level 1** sanal makinesine yönelik gerçekleştirilen bir sızma testi (penetration test) çalışmasını ve raporunu içermektedir.

## 🚀 Proje Hakkında

Bu çalışma, **Kali Linux** saldırı makinesi kullanılarak hedef sistemdeki zafiyetlerin tespit edilmesi, analiz edilmesi ve **Metasploit Framework** kullanılarak sömürülmesi (exploitation) süreçlerini kapsamaktadır.

Hedef makine olan **Kioptrix Level 1**, özellikle eski Samba sürümlerindeki açıklardan faydalanılarak ele geçirilmiş ve "Root" yetkisine ulaşılmıştır.



---

## 🎯 Projenin Amacı

Bu projenin temel amacı, siber güvenlik alanında aşağıdaki yetkinlikleri geliştirmek ve belgelemektir:
* Sanallaştırma ortamında (VMware) laboratuvar kurulumu.
* Ağ keşfi ve hedef belirleme.
* Port taraması ve servis versiyon tespiti (Enumeration).
* Zafiyet analizi ve uygun exploit'in seçilmesi.
* Metasploit Framework ile sisteme sızma.
* Sistem üzerinde yetki yükseltme ve bayrak (flag) tespiti.

---

## 🛠️ Kullanılan Araçlar ve Teknikler

* **İşletim Sistemleri:** Kali Linux (Saldırgan), Kioptrix Level 1 (Hedef)
* **Ağ Tarama:** `netdiscover`, `ifconfig`, `Nmap`
* **Sızma Aracı:** Metasploit Framework (`msfconsole`)
* **Kullanılan Exploit:** `exploit/linux/samba/trans2open`
* **Payload:** `generic/shell_reverse_tcp`

---

## 📝 Sızma Adımları (Walkthrough)

Bu çalışmada izlenen adımlar şunlardır:

1.  **Hazırlık:** Kali ve Kioptrix makinelerinin aynı ağ üzerinde çalıştırılması.
2.  **Keşif (Reconnaissance):** `ifconfig` ile kendi IP adresimizin tespiti ve ağdaki diğer cihazların bulunması.
3.  **Tarama (Scanning):** `nmap -sV` komutları ile hedef makinedeki açık portların (22, 80, 139, 443 vb.) tespiti.
4.  **Analiz:** 80 portundaki Web sayfasının incelenmesi ve 139 portundaki **Samba** servisine odaklanılması.
5.  **Exploit Seçimi:** Metasploit üzerinde `search samba` komutu ile uygun modülün (trans2open) bulunması.
6.  **Sızma (Exploitation):**
    * `use exploit/linux/samba/trans2open` modülünün seçilmesi.
    * `RHOST` ve `LHOST` ayarlarının yapılandırılması.
    * Payload'un 64-bit uyumluluğu için `generic/shell_reverse_tcp` olarak ayarlanması.
7.  **Sonuç:** Sisteme root yetkisiyle erişim sağlanması ve `/var/mail/root` dizinindeki tebrik mesajının okunması.

---

## 📸 Ekran Görüntüleri


### 1. Nmap Tarama Sonuçları
Hedef makinedeki açık portların (TCP 22, 80, 139, 443) tespit edildiği an.

![Nmap Scan Result](<img width="827" height="441" alt="image" src="https://github.com/user-attachments/assets/2f5a2891-0f6f-4522-8a92-4d4c167578a3" />
<img width="570" height="395" alt="image" src="https://github.com/user-attachments/assets/412d420d-a9fc-463e-bc3a-e4c98c92808b" />
)










### 2. Metasploit Ayarları ve Exploit Çalıştırma
Samba trans2open exploit'inin seçilmesi ve `run` komutu ile saldırının başlatılması.

![Metasploit Options](<img width="370" height="355" alt="image" src="https://github.com/user-attachments/assets/68ac2a3a-64b5-446a-8048-d212394af53d" />
)










### 3. Root Erişimi ve Onay Maili
Sisteme sızdıktan sonra root yetkisi ile okunan tebrik mesajı.

![Root Mail Success]( <img width="370" height="355" alt="image" src="https://github.com/user-attachments/assets/d6655acd-f09a-4b59-abd3-3c08b7aba6e0" />
)







---





## ⚠️ Yasal Uyarı

Bu proje tamamen **eğitim amaçlı** hazırlanmıştır. Sadece izin verilen, yasal laboratuvar ortamlarında (VulnHub, HackTheBox vb.) uygulanmalıdır. İzinsiz sistemlere sızmak yasa dışıdır.

---
