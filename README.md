# nodemcu-01
## 📌 Översikt
I detta projekt arbetar jag med NodeMCU (ESP8266) och Arduino IDE för att utföra grundläggande laborationer. Mitt mål är att förstå hur man programmerar en mikrocontroller, hur digitala portar fungerar och hur **setup()** och **loop()** bygger upp hela programstrukturen i Arduino.

Som exempel visar jag hur man gör ett enkelt **Blink-program**, det vill säga att tända och släcka en LED med jämna intervaller.

## 🔧 Mikroprocessor (som används)
Jag använder **NodeMCU med ESP8266-processorn**, som är en liten och billig mikrokontroller med:
- Inbyggt WiFi
- Flera digitala I/O-portar
- Enkel programmering via USB
- Stöd i Arduino IDE

Den fungerar som en mini-dator som kör instruktioner i en loop, och används ofta i IoT-projekt.

## ⚙️ Två basfunktioner i Arduino: `setup()` och `loop()`
Alla Arduino-program består av två huvuddelar: `setup()` och `loop()`. Man kan säga att dessa gör basen i varje sketch.

### 🟦 `setup()` – körs en gång
`setup()` körs endast en gång när programmet startar, t.ex. efter uppladdning eller när du trycker på reset.

Här gör man alla initialiseringar, t.ex:

- Ställa in vilka portar som är `INPUT` eller `OUTPUT`  
- Starta seriell kommunikation  
- Initiera sensorer och bibliotek  

**Exempel:**
```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT); /// Använder den inbyggda LED:en på NodeMCU
}
```

Tänk på `setup()` som "startinställningar" innan programmet börjar rulla.

### 🟩 loop() – körs om och om igen

`loop()` är huvudprogrammet. Efter att `setup()` körts startar `loop()` — och körs i en oändlig slinga så länge enheten är på.

Här lägger man allt som ska hända upprepade gånger:
- Tända/släcka LED
- Läsa sensorer
- Reagera på knapptryck
- Skicka data
- Köra logik, timers osv.

**Exempel:**
```cpp
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // Tänd LED
  delay(1000);             // Vänta 1 sekund
  digitalWrite(LED_BUILTIN, LOW);   // Släck LED
  delay(1000);             // Vänta 1 sekund
}
```
Här blinkar LED:en eftersom `loop()` upprepar detta block hela tiden.

## 💡 Blinkprogram – komplett exempel

Här är hela koden samlad i en sketchfil (`blink.ino`):

```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT); // Sätter den inbyggda LED:en som output
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH); // Tänd LED
  delay(1000);            // Vänta 1 sekund
  digitalWrite(LED_BUILTIN, LOW);  // Släck LED
  delay(1000);            // Vänta 1 sekund
}
```

Du kan ändra `delay()` om du vill att LED ska blinka snabbare eller långsammare.
