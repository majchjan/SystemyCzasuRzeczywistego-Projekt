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
   - `Aktuatory` – sterowanie silnikiem, zaworami, pompą.
3. **Wątki**:
   - `Obsługa_Użytkownika` – reakcja na przyciski panelu.
   - `Monitorowanie_Awarii` – wykrywanie błędów (np. przeciek).
4. **Dane**:
   - `Konfiguracja_Programu` – parametry wybranego cyklu prania.
5. **Urządzenia**:
   - `Silnik`, `Zawory_Wody`, `Grzałka` – fizyczne komponenty.

## Diagramy (do dodania)

## Autor
Jan Majchrowicz\
[GitHub/majchjan](https://github.com/majchjan)  

## Licencja
MIT