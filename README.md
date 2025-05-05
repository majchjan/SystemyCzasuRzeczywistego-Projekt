# Projekt Pralka Automatyczna w AADL - Systemy Czasu Rzeczywistego

Projekt realizowany w ramach przedmiotu **Systemy Czasu Rzeczywistego**, polegający na modelowaniu architektury pralki automatycznej przy użyciu języka **AADL** (Architecture Analysis & Design Language) w narzędziu **OSATE2**.

## Opis systemu
Pralka automatyczna to system czasu rzeczywistego, który:
- Steruje procesem prania (pobór wody, mieszanie detergentu, obrót bębna, odpompowywanie wody).
- Reaguje na zdarzenia użytkownika (wybór programu, start, pauza).
- Monitoruje parametry (temperatura, poziom wody, czas) za pomocą czujników.
- Wymaga synchronizacji między komponentami (np. blokada drzwi podczas pracy).

## Główne komponenty (w AADL)
1. **System** `Pralka_Automatyczna` – główny komponent zarządzający.
2. **Procesy**:
   - `Sterowanie_Cykle` – zarządza programami prania.
   - `Czujniki` – odczyt danych z sensorów (temperatura, poziom wody).
   - `Aktuatory` – kontrola elementów wykonawczych
   - `Obsługa_Użytkownika` – reakcja na przyciski panelu.
   - `Monitorowanie_Awarii` – wykrywanie błędów (np. przeciek).
   - `Zarządzanie_Energią` – minimalizacja zużycia energii podczas pracy.
3. **Wątki**:
   - `Wybór_Programu` – wybór i zapisywanie ustawień prania.
   - `Start_Stop_Pauza` – inicjowanie, zatrzymywanie i pauzowanie cyklu.
   - `Czujnik_Poziomu_Wody` – monitorowanie i regulacja poziomu wody.
   - `Czujnik_Temperatury` – nadzorowanie temperatury wody.
   - `Monitorowanie_Bębna` – kontrola prędkości i przeciążeń bębna.
   - `Bezpieczeństwo_Drzwi` – nadzór nad zamknięciem i blokadą drzwi.
   - `Sterowanie_Grzałką` – podgrzewanie wody do zadanej temperatury.
   - `Sterowanie_Zaworami` – włączanie/wyłączanie zaworów wody (pobór, odpływ).
   - `Sterowanie_Pompą` – odpompowywanie wody.
   - `Zarządzanie_Alarmami` – sygnalizacja błędów i zakończenia cyklu.

4. **Dane**:
   - `Konfiguracja_Programu` – parametry wybranego cyklu prania.
   (Do uzupełnienia)
5. **Urządzenia**:
   - `Silnik bębna`
   - `Zawory_Wlotowy`
   - `Grzałka_Wody`
   - `Pompa_Wody` - do odpompowywania wody po praniu
   - `Elektrozamek_Drzwi`
   - `Zawór_Nadmienego_Wyplywu` - awaryjne spuszczanie wody w przypadku przepełnienia.
   - `Alarm_Dzwiekowy` - na rozpoczęcie i zakończenie pracy oraz w przypadku awarii
   - `Czujnik_Temperatury`
   - `Czujnik_Poziomu_Wody`
   - `Czujnik_Drzwi` - wykrywaniezamknięcia drzwi
   - `Czujnik_Wycieków` - wykrywanie wyciekającej wody
   - `Czujnik_Prędkości_Bębna` - monitoring obrotów bębna

## Diagramy (do dodania)

## Autor
- Jan Majchrowicz\
[GitHub/majchjan](https://github.com/majchjan)  

## Licencja
MIT