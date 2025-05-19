# Projekt Pralka Automatyczna w AADL - Systemy Czasu Rzeczywistego

Projekt realizowany w ramach przedmiotu **Systemy Czasu Rzeczywistego**, polegający na modelowaniu architektury pralki automatycznej przy użyciu języka **AADL** (Architecture Analysis & Design Language) w narzędziu **OSATE2**.

## Autor
- Jan Majchrowicz
   - GitHub: [GitHub/majchjan](https://github.com/majchjan)  
   - Email: majchrowiczj@student.agh.edu.pl

## Opis systemu
Pralka automatyczna to system czasu rzeczywistego, który musi reagować na zdarzenia w ściśle określonych przedziałach czasowych, gwarantując poprawne wykonanie cyklu prania.

### Wymagania funkcjonalne:
- Sterowanie procesem prania (pobór wody, dozowanie detergentu, obrót bębna, odpływ wody)
- Obsługa interakcji użytkownika (wybór programu, start/pauza/stop)
- Monitorowanie parametrów w czasie rzeczywistym (temperatura, poziom wody, prędkość bębna)
- Implementacja mechanizmów bezpieczeństwa (blokada drzwi, detekcja wycieków)
- Generowanie alarmów w sytuacjach awaryjnych

### Wymagania niefunkcjonalne:
- Czas reakcji na zdarzenia < 100ms
- Determinizm działania w trybach krytycznych
- Niskie zużycie energii w stanie bezczynności
- Odporność na zakłócenia elektromagnetyczne
- Modularna architektura umożliwiająca rozbudowę

## Główne komponenty (w AADL)
1. **System** `Pralka_Automatyczna` – główny komponent zarządzający. Zarządza komunikacją między komponentami.
2. **Procesy (Process)**:
   - `Sterowanie_Cykle` – zarządza programami prania.
   - `Czujniki` – odczyt danych z sensorów (temperatura, poziom wody).
   - `Aktuatory` – kontrola elementów wykonawczych
   - `Obsługa_Użytkownika` – reakcja na przyciski panelu.
   - `Monitorowanie_Awarii` – wykrywanie błędów (np. przeciek).
   - `Zarządzanie_Energią` – minimalizacja zużycia energii podczas pracy.

3. **Wątki (Thread) (periodic/aperiodic/sporadic)**:
   - `Wybór_Programu` (aperiodic) – obsługa wyboru programu
   - `Start_Stop_Pauza` (aperiodic) – sterowanie wykonaniem
   - `Czujnik_Poziomu_Wody` (periodic 500ms) – monitoring poziomu
   - `Czujnik_Temperatury` (periodic 1s) – kontrola temperatury
   - `Monitorowanie_Bębna` (periodic 200ms) – nadzór nad bębnem
   - `Bezpieczeństwo_Drzwi` (sporadic) – kontrola mechanizmu blokady
   - `Sterowanie_Grzałką` (periodic 2s) – regulacja temperatury
   - `Sterowanie_Zaworami` (aperiodic) – zarządzanie przepływem wody
   - `Sterowanie_Pompą` (aperiodic) – kontrola odpływu
   - `Zarządzanie_Alarmami` (sporadic) – sygnalizacja zdarzeń

4. **Dane (Data)**:
   - `Typ_Programu` - definicja struktury programu prania
   - `Konfiguracja` - parametry systemowe
   - `Dane_Sensorowe` - format danych z czujników
   - `Status_Systemu` - bieżący stan pralki
   - `Dane_Sterujące` - wartości sterujące aktuatorami

5. **Przepływy danych (Flows)**

- `Czujnik_Temperatury` --> `Sterowanie_Grzałką` [flow path]
- `Czujnik_Poziomu` --> `Sterowanie_Zaworami` [flow path]
- `Obsługa_Użytkownika` --> `Sterowanie_Cykle` [event port]
- `Monitorowanie_Bębna` --> `Monitorowanie_Awarii` [data port]
- `Aktuatory` --> `Silnik_Bębna` [command flow]

6. **Urządzenia (Hardware)**:
   - Procesor (Processor):
      - `CPU_Main` (100MHz)
   
   - Pamięć (Memory)
      - `RAM` (8MB)
      - `ROM` (4MB Flash)

   - Magistrale (Bus)
      - `Bus_Data`
      - `Bus_Control`

   - Urządzenia (Device)
      - `Silnik_Bębna`
      - `Zawór_Wlotowy`
      - `Grzałka_Wody`
      - `Pompa_Wody` - do odpompowywania wody po praniu
      - `Elektrozamek_Drzwi`
      - `Moduł_Alarmowy`
      - `Alarm_Dzwiekowy` - na rozpoczęcie i zakończenie pracy oraz w przypadku awarii
      - Czujniki:
         - `Czujnik_Temperatury`
         - `Czujnik_Poziomu_Wody`
         - `Czujnik_Drzwi` - wykrywanie zamknięcia drzwi
         - `Czujnik_Wycieków` - wykrywanie wyciekającej wody
         - `Czujnik_Prędkości_Bębna` - monitoring obrotów bębna

## Diagramy (do dodania)

## Literatura
[https://mlodytechnik.pl/archiwum/04-2004_jak_dziala.pdf](https://mlodytechnik.pl/archiwum/04-2004_jak_dziala.pdf)
[https://pmc.ncbi.nlm.nih.gov/articles/PMC11672837/pdf/antibiotics-13-01227.pdf](https://pmc.ncbi.nlm.nih.gov/articles/PMC11672837/pdf/antibiotics-13-01227.pdf)
[https://pmc.ncbi.nlm.nih.gov/articles/PMC11664346/pdf/RA-014-D4RA07365G.pdf](https://pmc.ncbi.nlm.nih.gov/articles/PMC11664346/pdf/RA-014-D4RA07365G.pdf)
## Licencja
MIT