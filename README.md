# Sistem inteligent de monitorizare și optimizare a consumului energetic la nivel de consumator rezidențial

[cite_start]**Absolvent:** VLAD Ionuț-Cristian [cite: 560]
**Conducători științifici:** Conf.dr.ing. ARGATU Florin-Ciprian, Conf.dr.ing. [cite_start]ADOCHIEI Felix [cite: 561, 562]
[cite_start]**Instituție:** Universitatea Națională de Știință și Tehnologie POLITEHNICA București [cite: 556]
[cite_start]**Facultatea:** Inginerie Electrică [cite: 556]
[cite_start]**Anul:** 2025 [cite: 564]

---

## Introducere

[cite_start]Lucrarea de față își propune să găsească o soluție pentru societatea aflată în evoluție continuă, atât din punct de vedere al tehnologizării, cât și al diversificării nevoilor individuale[cite: 616]. [cite_start]Automatizarea locuinței și monitorizarea consumului de energie electrică devin din ce în ce mai relevante pentru eficiența energetică, reducerea costurilor și protejarea mediului[cite: 617].

[cite_start]În acest context, soluțiile de tip **smart home**, precum cele bazate pe platforma **Home Assistant**, reprezintă un pas necesar pentru adaptarea la noile cerințe tehnologice și sustenabile[cite: 618]. [cite_start]Principala motivație a acestui proiect este nevoia urgentă de a înțelege și controla consumul de energie electrică, în special în contextul european unde eficiența energetică este prioritară[cite: 619].

[cite_start]Proiectul oferă o alternativă practică ce permite utilizatorilor să își evalueze consumul și să ia decizii pentru a reduce pierderile[cite: 622]. [cite_start]Sistemul combină microcontrolere (ESP32), protocoale de comunicare industriale (Modbus) și platforme software moderne (Grafana, InfluxDB) pentru a optimiza consumul energetic în timp real[cite: 633, 636].

---

## 1. Noțiuni teoretice

### 1.1. Metode de optimizare a eficienței energiei electrice
[cite_start]Metodele de optimizare se referă la utilizarea consumatorilor casnici cu un consum redus de energie[cite: 639]. [cite_start]În Uniunea Europeană, standardele reglementate după 1 martie 2021 clasifică aparatele pe o scară de la **A la G**, unde clasa A reprezintă eficiența maximă[cite: 640].

[cite_start]Pe lângă utilizarea aparatelor eficiente, lucrarea cercetează implementarea sistemelor de monitorizare bazate pe platforma **Arduino**, senzori și microcontrolere pentru vizualizarea și transmiterea datelor către sisteme de control[cite: 642, 643].

### 1.2. Protocoale de comunicație
[cite_start]Într-un sistem de comunicații, dispozitivele care schimbă informații se numesc entități de comunicație și respectă reguli standardizate numite protocoale[cite: 646, 647]. [cite_start]Acestea au rolul de a iniția, gestiona și controla comunicația, stabilind reguli pentru reprezentarea datelor, semnalizare și detecția erorilor[cite: 650].

#### 1.2.1 Protocoale de comunicație fără fir (Wireless)
[cite_start]Acestea elimină necesitatea conexiunilor fizice, utilizând unde electromagnetice (frecvențe radio sau microunde)[cite: 653, 654]. [cite_start]Sunt esențiale pentru sistemele care necesită mobilitate ridicată[cite: 655].

*Fig.1.1. [cite_start]Protocoale de comunicație fără fir* [cite: 657]

**Tehnologia Wi-Fi (IEEE 802.11):**
[cite_start]Reprezintă una dintre cele mai utilizate soluții pentru rețele locale, susținând de la telefoane și laptopuri până la echipamente IoT[cite: 658, 659]. [cite_start]A evoluat constant, oferind viteze ridicate (peste 600 Mbps în standardele moderne) și ușurință în configurare[cite: 660, 661].

*Fig.1.2. [cite_start]Rețea de tip Wi-Fi* [cite: 611]
