# Skrypt do prezentacji notebooka: rezonans stochastyczny

## 1. Wprowadzenie

Dzień dobry. W tej prezentacji pokazuję wizualizację zjawiska rezonansu stochastycznego w potencjale bistabilnym.

Główna idea jest trochę nieintuicyjna: zwykle szum kojarzy się z czymś, co pogarsza sygnał. W rezonansie stochastycznym pewien dobrze dobrany poziom szumu może jednak pomóc układowi lepiej reagować na słaby sygnał okresowy.

W notebooku analizuję cząstkę znajdującą się w potencjale z dwiema studniami. Cząstka może przebywać w lewej albo prawej studni, a między nimi znajduje się bariera potencjału. Słaby sygnał okresowy moduluje wysokość tej bariery, a szum umożliwia losowe przejścia między studniami.

## 2. Podstawowe pojęcia

Na początku notebooka znajduje się krótki słownik pojęć.

Potencjał bistabilny oznacza układ z dwoma stabilnymi stanami. W naszym przypadku są to dwie studnie: lewa i prawa.

Bariera potencjału to „wzgórze” między tymi studniami. Im wyższa bariera, tym trudniej cząstce przejść do drugiej studni.

Wymuszenie okresowe to słaby sygnał sinusoidalny. Samo wymuszenie nie jest wystarczająco silne, żeby deterministycznie przerzucać cząstkę między studniami. Ono tylko okresowo ułatwia przejście w jedną albo drugą stronę.

Szum stochastyczny to losowe zaburzenie o natężeniu oznaczanym jako `D`. Właśnie badamy, jak zmiana `D` wpływa na odpowiedź układu.

## 3. Potencjał i okresowa zmiana bariery

Pierwsza część wizualizacji pokazuje potencjał bistabilny w kilku fazach wymuszenia.

Na wykresie widać, że potencjał ma dwie studnie. W zależności od fazy sygnału okresowego jedna bariera jest obniżana, a druga podwyższana.

To jest kluczowe dla całego zjawiska. Gdy bariera w jedną stronę jest niższa, szum łatwiej może „przepchnąć” cząstkę do drugiej studni. Pół okresu później sytuacja się odwraca.

Dlatego oczekujemy, że przy odpowiednim poziomie szumu przejścia będą pojawiały się w rytmie wymuszenia okresowego.

## 4. Model dwustanowy i równanie Master

Następnie notebook przechodzi do uproszczonego modelu dwustanowego.

Zamiast śledzić dokładne położenie cząstki, rozróżniamy tylko dwa stany: lewa studnia, oznaczana jako `-1`, oraz prawa studnia, oznaczana jako `+1`.

Prawdopodobieństwo przebywania w prawej studni oznaczamy jako `n_+(t)`. Jego zmiany opisuje równanie Master.

Szybkości przejść między studniami są opisane wzorem Kramersa. Oznacza to, że im niższa chwilowa bariera i im większy szum `D`, tym większa szansa przejścia.

Ten model jest prostszy niż pełna symulacja ruchu cząstki, ale zachowuje najważniejszą informację: kiedy układ przeskakuje między dwoma stabilnymi stanami.

## 5. Wymuszenie okresowe i odpowiedź układu

Kolejna sekcja pokazuje bezpośredni związek między wejściem a wyjściem.

Na pierwszym wykresie widzimy sygnał wejściowy, czyli funkcję okresową.

Następnie pokazana jest średnia odpowiedź układu, czyli `2n_+(t)-1`. Ta wielkość przyjmuje wartości od `-1` do `+1` i mówi, czy układ średnio jest bardziej w lewej, czy w prawej studni.

Potem pojawia się sygnał dwustanowy `y(t)`. Jest on równy `+1`, gdy cząstka jest w prawej studni, oraz `-1`, gdy jest w lewej.

Ten sygnał dobrze podkreśla momenty przejścia cząstki między studniami. Dzięki temu łatwo ocenić, czy przejścia zachodzą w rytmie sygnału wejściowego.

## 6. Symulacja Langevina

Po modelu dwustanowym notebook pokazuje pełniejszą symulację trajektorii cząstki za pomocą równania Langevina.

Tutaj `x(t)` oznacza rzeczywiste położenie cząstki. Jeśli `x(t)` jest ujemne, cząstka znajduje się w lewej studni. Jeśli jest dodatnie, znajduje się w prawej studni.

Równanie Langevina ma trzy składniki.

Pierwszy składnik wynika z potencjału bistabilnego i przyciąga cząstkę do jednej ze studni.

Drugi składnik to słabe wymuszenie okresowe.

Trzeci składnik to szum losowy o natężeniu `D`.

Na wykresach widać sygnał wejściowy, trajektorię `x(t)` oraz odpowiadający jej sygnał dwustanowy `y(t)`.

## 7. Widmo mocy

Następnie analizuję widmo mocy sygnału wyjściowego.

Widmo mocy pokazuje, jakie częstości są obecne w sygnale. Jeżeli układ dobrze odpowiada na wymuszenie okresowe, w widmie powinien pojawić się wyraźny pik przy częstości tego wymuszenia.

To jest bardzo ważne, bo z samego wykresu czasowego czasem trudno ocenić, czy odpowiedź jest naprawdę okresowa. Widmo pozwala zobaczyć to bardziej obiektywnie.

W rezonansie stochastycznym interesuje nas właśnie pik przy częstości wymuszenia. Jeżeli po dodaniu szumu ten pik rośnie, oznacza to, że szum wzmacnia odpowiedź układu na słaby sygnał.

## 8. Wpływ natężenia szumu

W kolejnej części porównuję kilka wartości szumu `D`.

Dla zbyt małego szumu cząstka rzadko przekracza barierę. Układ pozostaje zbyt długo w jednej studni, więc słaby sygnał okresowy jest słabo widoczny na wyjściu.

Dla pośredniego szumu przejścia zaczynają zachodzić wtedy, gdy bariera jest okresowo obniżana. To jest przypadek rezonansu stochastycznego.

Dla zbyt dużego szumu przejść jest bardzo dużo, ale są one chaotyczne i tracą związek z fazą sygnału wejściowego.

## 9. Wyznaczanie optymalnego D

Następnie notebook wyznacza optymalne natężenie szumu `D`.

Dla wielu wartości `D` obliczana jest moc składowej sygnału wyjściowego przy częstości wymuszenia.

Wynik jest pokazany jako `OUTPUT(dB)` w funkcji `D`.

Skala decybelowa jest znormalizowana tak, że najlepszy punkt ma wartość `0 dB`. Wartości ujemne oznaczają słabszą odpowiedź.

Maksimum tej krzywej wskazuje optymalny poziom szumu. W aktualnym uruchomieniu dla modelu Master optimum wypada około `D ≈ 0.383`.

To pokazuje najważniejszą własność rezonansu stochastycznego: odpowiedź układu nie rośnie stale wraz z szumem. Najlepsza jest pewna wartość pośrednia.

## 10. Studium trzech przypadków

Na końcu notebook zawiera studium trzech przypadków dla symulacji Langevina.

Pierwszy przypadek to brak szumu, czyli `D=0`.

Wtedy ruch jest prawie deterministyczny. Słaby sygnał okresowy nie wystarcza, żeby regularnie przerzucać cząstkę przez barierę. Sygnał dwustanowy prawie się nie zmienia.

Drugi przypadek to szum optymalny. Dla tej symulacji optymalna wartość wychodzi około `D ≈ 0.140`.

W tym przypadku szum pomaga cząstce przekraczać barierę wtedy, gdy wymuszenie okresowe ją obniża. Widać wyraźniejszą synchronizację z sygnałem wejściowym i silniejszą składową w widmie.

Trzeci przypadek to szum zbyt duży.

Tutaj cząstka przeskakuje często, ale w sposób bardziej przypadkowy. Na wykresie wygląda to jak chaos: dużo przejść nie oznacza dobrej odpowiedzi na sygnał.

## 11. Metryki porównawcze

W studium trzech przypadków pojawiają się też dodatkowe metryki.

Moc przy częstości wymuszenia mówi, jak silny jest okresowy składnik odpowiedzi.

Liczba przejść na okres pokazuje, jak często układ zmienia studnię.

Synchronizacja faz przejść mówi, czy przejścia zachodzą w podobnych fazach sygnału wejściowego.

To jest ważne, bo przy za dużym szumie liczba przejść może być duża, ale przejścia są przypadkowe. Z punktu widzenia rezonansu stochastycznego dobry szum to nie ten, który powoduje najwięcej przejść, ale ten, który powoduje przejścia najlepiej zsynchronizowane z wymuszeniem.

## 12. Wniosek końcowy

Cały notebook pokazuje, że w układzie nieliniowym z dwiema studniami szum może pełnić konstruktywną rolę.

Bez szumu słaby sygnał okresowy nie jest w stanie skutecznie przełączać układu między stanami.

Przy optymalnym szumie przejścia zachodzą w rytmie wymuszenia, a w widmie pojawia się wyraźny pik przy częstości sygnału.

Przy zbyt dużym szumie układ staje się chaotyczny i traci synchronizację.

To właśnie jest rezonans stochastyczny: maksimum odpowiedzi układu pojawia się dla niezerowego, ale nie za dużego poziomu szumu.

## 13. Krótkie zakończenie do powiedzenia

Podsumowując: pokazałem potencjał bistabilny z okresowo zmienną barierą, model dwustanowy, symulację Langevina, widma mocy oraz wyznaczenie optymalnego poziomu szumu. Najważniejszy wynik jest taki, że odpowiednio dobrany szum wzmacnia widoczność słabego sygnału okresowego, natomiast szum zbyt duży niszczy synchronizację i prowadzi do chaotycznych przejść.
