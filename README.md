## Architektura Potoku Przetwarzania (Krok po Kroku)

### Krok 1: Przygotowanie danych wejściowych
* **Plik:** `konwersja_mat_na_txt.ipynb`
* **Opis:** Służy do konwersji plików z rozszerzeniem `.mat` (pobranych bezpośrednio z platformy EPISODES) na format tekstowy `.txt`. Taki format jest wymagany jako wejście do dalszych skryptów środowiska MATLAB.

### Krok 2: Filtracja energetyczna wstrząsów
* **Plik:** `Setting_magnitude_treshold.ipynb`
* **Opis:** Nowy kod ustalony na ostatnim spotkaniu projektowym. Odpowiada za odrzucenie szumu i mikro-drgań poprzez usunięcie z głównego zbioru danych wszystkich wierszy, w których wartość magnitudy jest niższa niż zdefiniowany próg progowy (`magnitude_threshold`).

### Krok 3: Integracja danych i wstępna wizualizacja
* **Plik:** `creating_plots_and_csv_files.ipynb`
* **Opis:** Skrypt integrujący. Pobiera przetworzone dane z kodu MATLAB (który generuje `SSD` oraz `DC`), łączy rozproszone pliki w jedną spójną całość, generuje wstępne wykresy poglądowe i zapisuje wynik końcowy do czystego formatu `.csv`.

### Krok 4: Automatyczna detekcja i etykietowanie faz
* **Plik:** `fazy_automatycznie.ipynb`
* **Opis:** Algorytm realizujący automatyczny podział na fazy na podstawie założeń fizycznych (np. dopasowanych do rejonu Song Tranh). Szuka lokalnych szczytów energii SSD (koniec Fazy IV), cofa się w czasie do minimów DC (początek Fazy IV) oraz szuka głównego wstrząsu (*Mainshock*). Na tej podstawie automatycznie generuje wektor etykiet (`0` lub `1`), wycina fragmenty z odpowiednim zapasem kontekstu i zapisuje gotowe próbki treningowe.

### Krok 5: Manualna korekta i etykietowanie faz
* **Plik:** `fazy_recznie.ipynb`
* **Opis:** Narzędzie alternatywne lub uzupełniające dla kroku 4. Pozwala użytkownikowi na ręczne wskazanie i zdefiniowanie ram czasowych, w których występuje dana faza sejsmiczna, w przypadkach gdy automatyczna detekcja jest niewystarczająca.

### Krok 6: Walidacja i kontrola jakości
* **Plik:** `print_all_labeled_plots.ipynb`
* **Opis:** Ostatni krok w potoku przetwarzania. Służy do seryjnego wyświetlania wygenerowanych wcześniej wykresów z nałożonymi etykietami. Pozwala na szybką wizualną ocenę poprawności przygotowanych danych przed wgraniem ich do modelu uczenia maszynowego.
