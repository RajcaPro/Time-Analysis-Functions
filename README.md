# Time-Analysis-Functions
See what opportunities come with time series analysis functions! 🚀
------------

Cześć! 
W tym poście pokaże wam najważniejsze elementy analizy czasowej, jakie przydadzą się wam w projektowaniu raportów. Zapnijcie pasy.. SAMOLOT ODLATUJE 🚀🚀


Zacznijmy od YTD.

Można obliczyć wielkość sprzedaży od początku roku, modyfikując kontekst filtru dla dat, aby obejmował daty od 1 stycznia i kończył się w miesiącu odpowiadającymm obliczanej właśnie kommórce.

KOD:

![image](https://github.com/user-attachments/assets/abd3b353-1897-431d-b8e2-8d32d9ed79c7)

Szczegółowe wyjaśnienie składników:

CALCULATE

Jest to najważniejsza funkcja w DAX, która zmienia kontekst obliczeń.
W tym przypadku zmienia kontekst tak, by uwzględniał jedynie daty od początku roku do wybranej daty.

Sales[Sales Amount]

To kolumna lub miara, która zawiera wartości sprzedaży (np. kwoty transakcji).
CALCULATE zadziała na tych wartościach.

DATESYTD('Date'[Date])

To funkcja, która zwraca zestaw dat od początku roku (Year-To-Date) aż do aktualnie filtrowanej daty w raporcie.
Działa w oparciu o kolumnę dat z tabeli kalendarzowej ('Date'[Date]).

Jak to działa w praktyce?

Jeśli wybierzesz np. datę 15 marca 2024 w swoim raporcie:
Funkcja DATESYTD wybierze wszystkie daty od 1 stycznia 2024 do 15 marca 2024.
Funkcja CALCULATE przefiltruje dane sprzedaży tylko dla tych dat.
Wynik to suma sprzedaży od początku roku do 15 marca 2024.

Efekt : 

![image](https://github.com/user-attachments/assets/338689b6-fa0f-454f-93e6-73521d7929f2)

Możemy również użyć funkcji TOTALYTD, da ona taki sam efekt co powyższa miara. Dzięki swojej nazwie można łatwo zorientować się co ona robi lecz warto jednak opanować działanie oryginalnej składni używającej
CALCULATE, gdyż pozwala ona na wykonywanie barziej zaawansowanych obliczeń. 

![image](https://github.com/user-attachments/assets/02c27452-105e-4964-bf16-514b96f90f1b)

![image](https://github.com/user-attachments/assets/5db14a51-d13f-43b9-a79e-924651269a9e)

TOTALYTD

Jest to gotowa funkcja DAX do obliczania wartości skumulowanej od początku roku do określonej daty.
Ułatwia pracę, bo nie trzeba ręcznie używać CALCULATE i DATESYTD. Funkcja robi to automatycznie.

Podobnie jak w przypadku obliczeń o początku roku, dostępne są funkcje wbudowane od początku kwartału, miesiąca : TOTALQTD, TOTALMTD. Patrz poniżej:

![image](https://github.com/user-attachments/assets/b8ba00aa-199a-40e1-b3a9-53bb1271bea8)


Przejdźmy teraz do OBLICZANIA WARTOŚCI DLA WCZEŚNIEJSZYCH OKRESÓW.

Użytkownicy końcowi raportu często potrzebują porównać zagregowane wartości dla anakigicznego okresu roku poprzedniego - PY.

Język DAX udostępnia zaawansowaną funkcję realizującą to zadanie :




