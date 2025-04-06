# OpenBook - Cititor ePaper cu ESP32-C6

## Prezentare

OpenBook este un eBook reader simplu si eficient, gandit pentru cei care vor o experienta de lectura fara distrageri. Proiectat in jurul microcontrollerului ESP32-C6, dispozitivul vine cu un ecran e-paper de 7.8 inch, ideal pentru afisarea clara a textelor in orice conditii de lumina.

Alimentarea se face printr-o baterie Li-Po de 3.7V, cu incarcare prin USB-C, iar navigarea printre pagini se realizeaza cu ajutorul butoanelor fizice, pentru o interactiune directa si intuitiva. In plus, cititorul dispune de un slot microSD pentru stocarea cartilor, un senzor BME680 pentru monitorizarea mediului si un LED pentru semnalizari vizuale.

Interfata este gandita sa fie cat mai clara si usor de folosit, controlata prin GPIO-uri, astfel incat sa te poti concentra pe ceea ce conteaza: lectura.

OpenBook este un dispozitiv compact, eficient energetic si usor de integrat in orice rutina de lectura zilnica.


## Caracteristici Tehnice

- **Controller principal**: ESP32-C6 (cu suport Wi-Fi 6, BLE si arhitectura RISC-V)
- **Display**: E-paper cu diagonala de 7.8"
- **Senzori inclusi**: BME680 - masoara temperatura, umiditate, presiune atmosferica si compusi gazosi
- **Alimentare**: Acumulator Li-Po 3.7V, reincarcabil prin USB-C
- **Timp real**: Ceas RTC extern pentru functionare in deep sleep
- **Control utilizator**: 3 butoane fizice + LED
- **Memorie externa**: microSD
- **Interfete disponibile**: USB-C si Qwiic

---


## Pasii de implementare

1. Realizarea schemei electronice.
2. Aranjarea componentelor pe placa PCB (2D)
3. Verificare ERC si DRC, corectarea erorilor aparute.
4. Rutare.
5. Decupaj sub antena ESP32 si eliminarea planului de masa din acea zona.
6. Proiectarea modelului tridimensional.
7. Integrarea PCB-ului intr-o carcasa 3D compatibila.
8. Realizarea bateriei si a display-ului.
9. Randare si simulare a prototipului final
---

## Estimare Consum Energetic

Mai jos sunt prezentate valorile medii de consum pentru principalele componente ale dispozitivului, atat in modul activ, cat si in repaus:

| Componenta            | Consum mediu            | Activ / Idle                         |
|----------------------|--------------------------|--------------------------------------|
| **ESP32-C6**         | ~80 mA                   | 130 mA activ / 12 µA in deep sleep   |
| **E-paper 7.8**     | ~26 mA in timpul refresh-ului | 0 mA in repaus                     |
| **Senzor BME680**    | ~2.1 mA                  | 0.15 mA in standby                   |
| **Card microSD**     | ~30-100 mA (in utilizare) | 0.1 mA in modul sleep               |
| **RTC + supercapacitor** | ~1 µA               | -                                    |
| **LED**              | max. ~10 mA              | Consumabil doar cand este activ     |

###  Total Estimat:
- **In utilizare activa**: ~100-150 mA
- **In modul deep sleep**: ~15 µA

###  Autonomie estimata (baterie 1200 mAh):
- **Utilizare activa, cu refresh ocazional**: aproximativ **8-10 ore**
- **Predominant in deep sleep**: pana la **300 de zile** in standby


##  Diagrame si Scheme

![image.png](https://github.com/alexiamihai/TSC---ebookReader/blob/main/Images/DIAGRAMA.png)

---

## Lista Componentelor (BOM)

# List of Components

Componentele utilizate in proiect sunt prezentate mai jos, alaturi de linkuri utile pentru verificarea preturilor si a fiselor tehnice. In cazurile in care nu a fost specificat un model exact, campurile corespunzatoare apar marcate cu **#N/A**.

| Name of component  | Device                                    | Check Prices                                                                 | DataSheet                                                                  |
|--------------------|-------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|
| BOOT_BUTTON        | BUTTON_CUSYOMV1                           | [Check Price](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) |
| C1                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | [Check Price](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) |
| C1_BAT             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C1_BAT1            | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C1_BAT2            | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C2                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C2_BAT\            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C3                 | RCL_CPOL-EUCT3528                         | #N/A                                                                         | #N/A                                                                      |
| C4                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C4_USB             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C5                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C5_USB             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C6                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C7                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C8                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C9                 | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C10                | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C10_SUPERCAP       | CPH3225A                                  | [Check Price](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) |
| CHANGE_BUTTON      | BUTTON_CUSYOMV1                           | [Check Price](https://industry.panasonic.com/global/en/products/control/switch-light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch-light-touch/number/evqpuj02k) |
| CHG_LED            | ADAFRUIT_LEDCHIP-LED0603                  | [Check Price](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) | [DataSheet](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) |
| C_DELAY            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| D1                 | USBLC6-2SC6Y                              | [Check Price](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) |
| D2                 | ESP32_WROVER_AVX---SD0805S020S1R0_AVX_... | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](http://datasheets.avx.com/schottky.pdf)                       |
| D3                 | MBR0530                                   | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) |
| D4                 | MBR0530                                   | [Check Price](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| D5                 | MBR0530                                   | [Check Price](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| D6                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D7                 | ESP32_WROVER_AVX---SD0805S020S1R0_AVX_... | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](http://datasheets.avx.com/schottky.pdf)                       |
| D8                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D9                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D10                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D11                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D12                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| EPD_C1             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C2             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C5             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C6             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C7             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C8             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C9             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C10            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C11            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C12            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| IC1                | BD5229G-TR                                | [Check Price](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) | [DataSheet](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) |
| IC4                | XC6220A331MR-G                            | [Check Price](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [DataSheet](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |
| J1                 | FH34SRJ-24S-0.5SH_99_                     | [Check Price](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [DataSheet](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |
| J2                 | SAMACSYS_PARTS_USB4110-GF-A               | [Check Price](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)) | [DataSheet](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)) |
| J3                 | QWIIC_CONNECTORJS-1MM                     | #N/A                                                                         | #N/A                                                                      |
| J4                 | 112A-TAAR-R03_ATTEND                      | [Check Price](https://store.comet.srl.ro/Catalogue/Product/43497/)           | [DataSheet](https://store.comet.srl.ro/Catalogue/Product/43497/)          |
| L1                 | 744043680IND_4828-WE-TPC_WRE              | [Check Price](https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) | [DataSheet](https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) |
| PFMF.050.1         | ESP32C6_VARISTORCN1812                    | [Check Price](https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D) | [DataSheet](https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D) |
| Q1                 | ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_... | [Check Price](https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated) | [DataSheet](https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated) |
| Q2                 | ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_... | #N/A                                                                         | #N/A                                                                      |
| Q3                 | D8                                        | [Check Price](https://componentsearchengine.com/part-view/PGB1010603MR/Littelfuse) | [DataSheet](https://componentsearchengine.com/part-view/PGB1010603MR/Littelfuse) |
| Q4                 | Q2_TS-B2_REACHPACK                        | #N/A                                                                         | #N/A                                                                      |


### Descrierea hardware -- Conexiuni si Functionalitate

1.  **USB-C Connector & ESD Protection**\
    Conectorul USB-C permite atat programarea ESP32-C6, cat si incarcarea bateriei prin VBUS. Se conecteaza la MCP73831 pentru incarcarea bateriei si la ESP32-C6 pentru programare. Pinii ESP32-C6 implicati sunt IO13 (USB_D-) si IO14 (USB_D+).

2.  **Li-Po Battery + MCP73831 (Battery Charging Controller)**\
    Bateria Li-Po este gestionata de MCP73831 pentru incarcare si furnizarea de energie intregului sistem. MCP73831 este conectat la un regulator LDO care asigura tensiunea de 3.3V pentru ESP32-C6. LED-ul de incarcare este controlat de pinul IO4.

3.  **XC6220 (LDO Voltage Regulator)**\
    Regulatorul de tensiune LDO asigura o tensiune stabila de 3.3V, esentiala pentru functionarea corecta a componentelor digitale. Se conecteaza la MCP73831 si furnizeaza alimentare la ESP32-C6.

4.  **W25Q512 (External NOR Flash)**\
    Memoria flash externa W25Q512 este utilizata pentru stocarea datelor persistente. Este conectata la ESP32-C6 prin SPI, avand pini pentru semnalul de ceas (SCK), datele de iesire (MOSI), datele de intrare (MISO) si selectarea chipului (CS).

5.  **E-Paper Display Header & Driver**\
    Ecranul e-paper este controlat prin SPI, avand semnale suplimentare pentru controlul de stare. Pinii IO6, IO7 si IO2 sunt folositi pentru comunicarea SPI, iar pini suplimentari sunt utilizati pentru semnalele de comanda (DC), ocupare (BUSY) si resetare (RST).

6.  **MicroSD Card**\
    Cardul microSD este folosit pentru stocarea de fisiere externe, cum ar fi texte sau resurse. Foloseste aceleasi pini SPI partajati cu alte periferice (SCK, MOSI, MISO), cu un pin dedicat pentru selectarea cardului (CS_SD).

7.  **RTC DS3231SN**\
    Ceasul RTC DS3231SN ofera o masuratoare precisa a timpului, chiar si in modul de repaus al ESP32-C6. Acesta este conectat la ESP32-C6 prin I2C si include pini pentru intreruperi (INT_RTC) si reset (RTC_RST), permitand trezirea automata a sistemului.

8.  **BME680 -- Environmental Sensor**\
    Senzorul BME680 masoara temperatura, umiditatea, presiunea si calitatea aerului. Acesta este conectat la ESP32-C6 prin I²C, avand pini partajati cu RTC pentru comunicarea datelor.

9.  **Butoane de control (BOOT, CHANGE, RESET)**\
    Butoanele de control permit utilizatorului sa interactioneze cu sistemul. Pinul BOOT (IO15) este folosit pentru programare, pinul RESET (IO3) pentru a reseta sistemul, iar pinul CHANGE (IO23) permite schimbarea optiunilor sau navigarea prin interfata.

10. **Voltage Supervisor & IO**\
    Supraveghetorul de tensiune monitorizeaza tensiunile critice si protejeaza sistemul in timpul pornirii si resetarii. Acesta este conectat la pinul IO1, IO18 si IO22 de pe ESP32-C6, asigurand functionarea corecta a circuitului.

11. **Battery Level Monitor**\
    Monitorizarea nivelului bateriei se realizeaza prin intermediul unui pin ADC (IO18) care masoara tensiunea bateriei. Aceste informatii sunt folosite pentru a trimite notificari utilizatorului sau pentru a inregistra nivelul bateriei.

12. **Qwiic / Stemma QT Connector**\
    Conectorul Qwiic / Stemma QT permite extinderea sistemului prin adaugarea de senzori I2C suplimentari, fara a necesita lipirea firelor. Acesta este conectat la ESP32-C6 prin pini I2C(SDA si SCL).

13. **Serial (TX/RX)**\
    Conexiunea seriala UART (TX/RX) este folosita pentru debug si comunicare intre ESP32-C6 si un PC sau terminal. Pinul TX (IO25) trimite date catre PC, iar pinul RX (IO24) primeste date de la PC.


### Pinout ESP32-C6

1.  **IO2 -- MISO (SPI)**\
    Acest pin este utilizat pentru comunicarea SPI, fiind dedicat transferului de date catre microcontroller dinspre perifericele externe, cum ar fi Flash NOR, E-Paper si microSD. Asigura viteza si compatibilitate nativa pentru aceste dispozitive.

2.  **IO6 -- SCK (SPI Clock)**\
    Pinul IO6 este folosit ca semnal de ceas (SCK) in protocolul SPI, esential pentru sincronizarea transferurilor de date. Este recomandat pentru a partaja magistrala SPI intre diferite periferice, precum Flash NOR, E-Paper si microSD.

3.  **IO7 -- MOSI (SPI Data Out)**\
    Acest pin transmite date catre perifericele conectate prin SPI. Este folosit de dispozitivele Flash NOR, E-Paper si microSD pentru a primi informatiile necesare, oferind o comunicatie rapida.

4.  **IO4 -- CS_SD**\
    Pinul CS_SD selecteaza cardul microSD pentru citirea datelor. Utilizarea acestui pin permite evitarea conflictelor cu alte periferice SPI, asigurand o accesibilitate exclusiva la cardul SD in timpul operatiunii de citire sau scriere.

5.  **IO12 -- CS Flash**\
    Acest pin este utilizat pentru a activa memoria Flash externa. Este dedicat selectarii si initializarii memoriei NOR Flash, permitand un acces rapid si sigur la stocarea externa.

6.  **IO10 -- CS EPD**\
    Pinul CS EPD este folosit pentru a selecta afisajul E-Paper in timpul transferurilor de date prin SPI. Asigura ca ecranul este adresabil si se poate comunica cu el in mod eficient.

7.  **IO5 -- DC (Data/Command pentru EPD)**\
    Semnalul DC controleaza diferentierea intre comenzi si date in cazul afisajului E-Paper. Acest pin permite gestionarea corecta a fluxului de informatii intre microcontroller si ecran.

8.  **IO14 -- EPD_BUSY**\
    Pinul EPD_BUSY este un semnal de stare care indica daca ecranul E-Paper este ocupat. Permite sistemului sa astepte finalizarea operatiunilor curente ale ecranului inainte de a trimite noi comenzi.

9.  **IO21 -- EPD_RST**\
    Acest pin este utilizat pentru a reseta afisajul E-Paper inainte de initializarea sa. Este important pentru a asigura o pornire corecta si o performanta optima a display-ului.

10. **IO19 -- SDA (I2C)**\
    Pinul SDA face parte din magistrala I2C si este utilizat de senzori precum RTC, BME680 si Qwiic pentru a trimite si primi date. Acesta este partajat intre mai multi senzori, permitand comunicarea eficienta.

11. **IO20 -- SCL (I2C)**\
    Pinul SCL este linia de ceas in protocolul I2C, sincronizand comunicatiile dintre dispozitivele conectate la magistrala I2C, inclusiv RTC si BME680.

12. **IO0 -- INT RTC**\
    Acest pin este un semnal de intrerupere care permite ESP32-C6 sa trezeasca din starea de deep sleep atunci cand RTC detecteaza un eveniment semnificativ, precum un schimb de timp sau o alarma.

13. **IO17 -- RTC Reset**\
    Pinul RTC Reset este folosit pentru a efectua un reset extern al RTC (Real Time Clock). Acest pin asigura sincronizari initiale corecte pentru ceasul RTC, garantand acuratetea masuratorilor de timp.

14. **IO15 -- BOOT**\
    Pinul BOOT este utilizat pentru a introduce ESP32-C6 in modul de programare. Acesta permite incarcarea unui firmware nou pe microcontroller.

15. **IO3 -- RESET**\
    Pinul RESET permite resetarea manuala a microcontrollerului ESP32-C6. Acesta poate fi folosit pentru a reporni sistemul in caz de erori sau modificari ale configurarii.

16. **IO23 -- Buton CHANGE**\
    Pinul IO23 este folosit pentru un buton de schimbare in interfata utilizatorului. Acesta poate fi utilizat pentru a naviga prin optiuni sau a schimba paginile in aplicatii.

17. **IO25/IO24 -- UART TX/RX**\
    Pinii IO25 si IO24 sunt folositi pentru comunicatia seriala UART. Acestia permit ESP32-C6 sa comunice cu un PC sau terminal pentru debug si monitorizare.

18. **IO18 -- Battery Monitor**\
    Pinul IO18 este folosit pentru monitorizarea nivelului bateriei prin intermediul unui ADC (Analog-to-Digital Converter). Acest pin masoara tensiunea bateriei, permitand sistemului sa notifice utilizatorul sau sa inregistreze datele pentru analize ulterioare.



### Concluzie

Extrem de stresant, dar macar s-a terminat. Sper ca totul e okay. Slay!




