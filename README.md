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

![image](https://github.com/user-attachments/assets/0bf018da-6332-4c28-be64-d3c205e1b206)

![image](https://github.com/user-attachments/assets/238c4cb4-b5e1-49dc-9966-fde67261a60a)

SAMEPEROIDLASTYEAR zwraca zbiór dat odpowiadający aktualnie wybranemu, przesuniętemu o jeden krok wstecz.
Jest to specjalizowana wersja ogólnej funkcji DATEADD. Możemy więc zdefiniować tę samą miarę PY sales przy użyciu poniższego kodu :

![image](https://github.com/user-attachments/assets/c3dc1f26-b9ab-45f3-b52e-dd1fab8daae3)

![image](https://github.com/user-attachments/assets/c7a0b6f2-d555-466e-920c-c1ac9ae00816)

W analogiczny sposób można obliczyć wartości dla poprzedniego kwartału PQ, miesiąca PM oraz dnia PD.

![image](https://github.com/user-attachments/assets/7ece5e13-d940-416d-8a4d-a84bac910879)

Zdarza się tak, że chcemy znaleźć całkowitą wartość miary dla poprzedniego roku. Z pomocą przychodzi PARALLELPEROID, który zwraca PEŁNY przedział wskazany przez trzeci parametr, zamiast częsciowego zwracanego przez DATEADD.

![image](https://github.com/user-attachments/assets/ebdabf6b-dbd8-4862-b6ac-96cecac22e6b)

![image](https://github.com/user-attachments/assets/3d3712a7-7aef-4c34-bac6-51de9a5ee29c)

W analogiczny sposób można obliczyć PQ, PM, PD.

![image](https://github.com/user-attachments/assets/c6d09215-7408-420c-bece-4807dce808e3)


Istnieją również funkcje podobne do PARALLELPEROID, które NIE SĄ IDENTYCZNE. 
Mowa o PREVIOUSYEAR, PREVIOUSQUARTER itd, oraz NEXTYEAR,NEXTQUARTER itd.

![image](https://github.com/user-attachments/assets/baecb1d9-ba82-4320-ab47-54b624d0f906)

różnica pomiędzy nimi jest widoczna na powyższym zdjęciu.
Miara  parallelperoid zwraca wartość dla grudnia 2007 zarówno dla całego roku 2008, jak i pierwszego kwartału 2008, podczas gdy PREVIOUSMONTH zawsze zwraca wyniki dla tej samej liczby wybranych miesięcy.

Ostatnim punktem tego wpisu będzie OBLICZANIE RÓŻNIC WZGLĘDEM WCZEŚNIEJSZYCH OKRESÓW.
Jeśli chcesz aby twój raport był uznawany za samo "mięso" musisz to wiedzieć! 📊✨

Do operacji typu MUST HAVE możemy zaliczyć znalezienie zmiany pomiędzy bieżącą wartości danej miary a jej wartości w roku poprzednim. Zmiany można zaprezentować jako różnicę albo wynik procentowy.

Różnica pomiędzy bieżącą wartością sprzedaży a wynikiem dla analogicznego okresu roku poprzedniego jest prostym odejmowaniem. Patrz poniżej :

![image](https://github.com/user-attachments/assets/1992c280-595e-442f-b1b8-725c094c0a28)

![image](https://github.com/user-attachments/assets/fefc01a5-db01-4b39-bac3-27196b8212a7)

![image](https://github.com/user-attachments/assets/df8a5150-1a23-46b7-90d7-5d8dec8dfee2)

a teraz zaprezentujmy zmianę procentową.

![image](https://github.com/user-attachments/assets/1ef2ab67-7c39-42a3-ade4-67faac9eb042)

![image](https://github.com/user-attachments/assets/bf56a7ab-ed30-49bb-9d01-2d324913292b)






