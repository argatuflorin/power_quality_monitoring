# Sistem Inteligent de Monitorizare și Optimizare Energetică (Smart Home)

Proiect de diplomă axat pe monitorizarea în timp real a consumului electric rezidențial și predicția acestuia folosind Inteligența Artificială (LSTM).

---

## Ce conține acest sistem:
- **Hardware:**
  - [cite_start]**ESP32-WROOM-32** (Unitatea centrală de control) [cite: 1180, 1228]
  - [cite_start]**Janitza UMG 104** (Analizor de rețea industrial) [cite: 1182, 1227]
  - [cite_start]**Convertor TTL la RS485 (MAX485)** (Interfața de comunicare) [cite: 1181, 1228]
- **Software:**
  - [cite_start]**Home Assistant** (Dashboard și control local) [cite: 1186, 1210]
  - [cite_start]**InfluxDB** (Stocarea datelor istorice) [cite: 1188, 1225]
  - [cite_start]**Grafana** (Vizualizare avansată și alerte) [cite: 1189, 1225]
  - [cite_start]**Protocol MQTT** (Transfer de date rapid) [cite: 1187, 1225]
  - [cite_start]**Google Colab / Python** (Modelul de predicție AI) [cite: 1190, 1228]

---

## Step 1: Arhitectura Sistemului

Sistemul funcționează pe modelul **Master-Slave** prin protocolul **Modbus RTU**:
1. [cite_start]**Master (ESP32):** Trimite cereri periodice către analizorul Janitza prin magistrala RS485[cite: 1227, 572].
2. [cite_start]**Slave (Janitza UMG 104):** Măsoară parametrii electrici (tensiune, curent, putere) și răspunde cererilor[cite: 1227, 573].
3. [cite_start]**Cloud/Local:** ESP32 trimite datele prin Wi-Fi către un server Home Assistant folosind protocolul MQTT[cite: 1225, 602].

---

## Step 2: Conexiuni Hardware (Wiring)

Pentru a realiza comunicația între ESP32 și Janitza UMG 104, trebuie să conectezi pinii conform tabelului de mai jos:

| Componentă | Pin ESP32 | Descriere |
| :--- | :--- | :--- |
| **MAX485 RO** | RX2 (GPIO16) | [cite_start]Receivier Output (Recepție date) [cite: 547] |
| **MAX485 DI** | TX2 (GPIO17) | [cite_start]Driver Input (Transmisie date) [cite: 547] |
| **MAX485 DE/RE** | GPIO4 | [cite_start]Control direcție (legat împreună) [cite: 548] |
| **VCC** | 3.3V / 5V | [cite_start]Alimentare modul [cite: 1181] |

[cite_start]**Important:** Janitza UMG 104 utilizează portul RS485 (A, B) pentru a se lega la ieșirea convertorului MAX485[cite: 573].

---

## Step 3: Testarea Comunicării Modbus

După realizarea conexiunilor, folosește acest snippet de cod în **Arduino IDE** pentru a verifica dacă ESP32 poate citi un registru (de ex: Tensiunea pe L1) de la adresa 19000:

```cpp
#include <ModbusMaster.h>

#define MAX485_RE_DE 4
ModbusMaster node;

void preTransmission() { digitalWrite(MAX485_RE_DE, HIGH); }
void postTransmission() { digitalWrite(MAX485_RE_DE, LOW); }

void setup() {
  pinMode(MAX485_RE_DE, OUTPUT);
  digitalWrite(MAX485_RE_DE, LOW);
  
  Serial.begin(115200);
  Serial2.begin(9600, SERIAL_8N1, 16, 17); // RX2=16, TX2=17
  
  node.begin(1, Serial2); // Adresa Modbus a Janitza (implicit 1)
  node.preTransmission(preTransmission);
  node.postTransmission(postTransmission);
}

void loop() {
  uint8_t result = node.readHoldingRegisters(19000, 2); // Citește tensiunea L1
  if (result == node.ku8MBSuccess) {
    Serial.println("Succes! Date recepționate de la Janitza.");
  } else {
    Serial.print("Eroare Modbus: ");
    Serial.println(result, HEX);
  }
  delay(1000);
}
