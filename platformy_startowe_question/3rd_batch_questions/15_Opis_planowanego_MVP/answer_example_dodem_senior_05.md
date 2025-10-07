### 1. Opis minimalnej, niskokosztowej wersji produktu (MVP) i plan walidacji rynkowej

**Opis MVP (Minimum Viable Product)**

Planowane MVP platformy Dodem to niskokosztowa, funkcjonalna wersja produktu, zaprojektowana w celu szybkiej weryfikacji kluczowych hipotez biznesowych i zebrania informacji zwrotnej od pierwszych użytkowników. MVP zostanie zrealizowane jako **aplikacja desktopowa na system Windows**, co odpowiada dominującemu środowisku technologicznemu grupy docelowej – seniorów.

**Kluczowe cechy i funkcjonalności MVP:**

1.  **Inicjacja pomocy:** Uproszczony mechanizm wzywania wsparcia, dostępny poprzez dedykowaną ikonę w zasobniku systemowym (system tray). Senior jednym kliknięciem sygnalizuje potrzebę pomocy, minimalizując barierę wejścia.
2.  **Sesja zdalna (podgląd):** Po zainicjowaniu pomocy, system automatycznie uruchamia **jednokierunkowy streaming ekranu** seniora do panelu webowego moderatora. Kluczowym założeniem jest brak możliwości przejęcia kontroli nad pulpitem seniora, co gwarantuje poczucie bezpieczeństwa i prywatności.
3.  **Mechanizm "Podpowiedzi kontekstowych w dymku" (Contextual Hints):**
    *   Moderator, widząc ekran seniora, wskazuje na swoim panelu konkretny element interfejsu (np. przycisk "Zaloguj", pole tekstowe, link).
    *   System (**Dodem AI Engine**) analizuje kontekst (zrzut ekranu, cel zadania) i generuje propozycję zwięzłej, jednoznacznej instrukcji.
    *   Moderator weryfikuje i akceptuje treść, a następnie wysyła **"dymek"** (graficzną podpowiedź ze strzałką) na ekran seniora.
    *   Senior wykonuje zadanie krok po kroku, prowadzony przez pojawiające się w odpowiednich miejscach instrukcje.
4.  **Logowanie zdarzeń:** System będzie zbierał zanonimizowane dane dotyczące interakcji (liczba sesji, czas trwania, liczba użytych "dymków", wskaźnik ukończenia zadań), które posłużą do analizy użyteczności i dalszego rozwoju produktu.

**Planowana walidacja rynkowa MVP:**

Proces walidacji został zaprojektowany w celu zebrania zarówno danych ilościowych, jak i jakościowych, które pozwolą na iteracyjne doskonalenie produktu.

*   **Grupa pilotażowa:** Testy zostaną przeprowadzone z udziałem **10-15 seniorów** rekrutowanych we współpracy z zaprzyjaźnionymi Uniwersytetami Trzeciego Wieku (UTW) oraz **3-5 moderatorów-wolontariuszy** (np. studenci informatyki, "rodzinni informatycy").
*   **Metody zbierania feedbacku:**
    *   **Dane ilościowe (metryki):** Automatycznie zbierane logi systemowe pozwolą śledzić kluczowe wskaźniki (Key Metrics), takie jak **Wskaźnik adopcji (Adoption Rate)**, **Czas do dostarczenia podpowiedzi (Time to Instruction)** oraz **Wskaźnik redukcji błędów (Error Reduction Rate)**.
    *   **Dane jakościowe:**
        *   **Ankiety satysfakcji:** Uczestnicy (seniorzy i moderatorzy) wypełnią krótkie ankiety po pierwszym i czwartym tygodniu testów, oceniając łatwość obsługi, przydatność "dymków" i ogólne zadowolenie.
        *   **Wywiady pogłębione:** Po zakończeniu pilotażu przeprowadzimy indywidualne wywiady z uczestnikami, aby dogłębnie zrozumieć ich doświadczenia, zidentyfikować bariery i zebrać sugestie dotyczące dalszego rozwoju.
*   **Kryteria sukcesu MVP:** Powodzenie MVP zostanie ocenione na podstawie osiągnięcia predefiniowanych celów:
    *   Wskaźnik adopcji na poziomie co najmniej 70% w grupie testowej.
    *   Średnia ocena satysfakcji użytkowników powyżej 4.0 w skali 5-punktowej.
    *   **Dokładność podpowiedzi (Hint Accuracy)** generowanych przez AI na poziomie >80% (oceniana przez moderatorów).

### 2. Zakres prac własnych i potrzeby w ramach inkubacji

**Prace zrealizowane w ramach zasobów własnych:**

Do tej pory, wykorzystując własne zasoby czasowe i finansowe, zrealizowaliśmy kluczowe etapy przygotowawcze:

*   **Analiza problemu i rynku:** Przeprowadziliśmy szczegółową analizę problemu **wykluczenia cyfrowego seniorów** oraz potrzeb rynkowych, co zostało udokumentowane w odpowiedziach na pytania z `1st_batch_questions`.
*   **Koncepcja rozwiązania:** Opracowaliśmy **Unikalną Propozycję Wartości (Unique Value Proposition)** oraz szczegółową koncepcję produktu, bazującą na mechanizmie "dymków", co opisano w `2nd_batch_questions`.
*   **Prototypowanie:** Stworzyliśmy klikalny prototyp interfejsu użytkownika w narzędziu Figma, który wizualizuje kluczowe funkcje i przepływy, umożliwiając wczesną weryfikację koncepcji.
*   **Nawiązanie relacji:** Zainicjowaliśmy rozmowy z potencjalnymi partnerami, w tym z kilkoma Uniwersytetami Trzeciego Wieku, które wyraziły wstępne zainteresowanie udziałem w programie pilotażowym.

**Potrzebne wsparcie w ramach inkubacji:**

Aby przekształcić zweryfikowaną koncepcję w działające MVP, potrzebujemy wsparcia w następujących obszarach:

*   **Usługi specjalistyczne (IT):** Kluczowym elementem jest sfinansowanie prac programistycznych, których nie jesteśmy w stanie zrealizować we własnym zakresie. Obejmuje to:
    *   Opracowanie backendu (API, baza danych, zarządzanie sesjami i użytkownikami).
    *   Stworzenie aplikacji desktopowej dla seniora (Windows).
    *   Zbudowanie panelu webowego dla moderatora.
*   **Wsparcie merytoryczne:**
    *   Konsultacje z ekspertami ds. **UX/UI dla seniorów** w celu zapewnienia maksymalnej dostępności i intuicyjności interfejsu.
    *   Doradztwo prawne w zakresie **RODO** i ochrony danych osobowych.
    *   Mentoring w obszarze **strategii biznesowej** i modelu subskrypcyjnego.
*   **Wsparcie organizacyjne:** Pomoc w formalizacji współpracy z partnerami (UTW) oraz w rekrutacji i koordynacji grupy pilotażowej.

### 3. Charakterystyka usług finansowanych z grantu

Wnioskujemy o udzielenie grantu na sfinansowanie zewnętrznych usług specjalistycznych, niezbędnych do stworzenia oprogramowania MVP.

*   **Nazwa usługi:** "Stworzenie oprogramowania MVP dla platformy asystenta cyfrowego Dodem"
*   **Szczegółowy zakres usługi:**
    1.  **Backend:** Zaprojektowanie i implementacja serwerowej części aplikacji, w tym:
        *   REST API do komunikacji między aplikacją seniora a panelem moderatora.
        *   System uwierzytelniania i zarządzania kontami użytkowników.
        *   Mechanizm zarządzania sesjami streamingu ekranu.
        *   Moduł do logowania zdarzeń i zbierania metryk.
    2.  **Aplikacja desktopowa (Windows) dla Seniora:**
        *   Prosty i czytelny interfejs użytkownika.
        *   Implementacja mechanizmu jednokierunkowego streamingu pulpitu.
        *   Implementacja warstwy do wyświetlania "dymków" (Contextual Hints) nad innymi aplikacjami.
    3.  **Aplikacja webowa (Panel) dla Moderatora:**
        *   Interfejs do podglądu streamu z ekranu seniora w czasie rzeczywistym.
        *   Narzędzia do interaktywnego wskazywania elementów na ekranie i wysyłania "dymków".
        *   Panel do weryfikacji i edycji instrukcji sugerowanych przez Dodem AI Engine.
*   **Czas realizacji:** 4 miesiące

### 4. Uzasadnienie szacowanego kosztu usługi

Przedstawiony szacunkowy koszt usługi został określony z należytą starannością, w oparciu o następujące przesłanki:

1.  **Analiza rynku:** Przeprowadziliśmy rozeznanie rynku usług programistycznych, analizując cenniki i portfolio kilku software house'ów specjalizujących się w tworzeniu aplikacji desktopowych i webowych.
2.  **Wstępne rozmowy:** Odbyliśmy wstępne, nieformalne konsultacje z potencjalnymi wykonawcami, którzy potwierdzili, że podany budżet jest realistyczny dla MVP o zdefiniowanym zakresie funkcjonalności.
3.  **Metodologia szacowania:** Koszt został skalkulowany na podstawie uśrednionych stawek rynkowych za godzinę pracy programisty (ok. 150-200 PLN netto/h) oraz szacowanej liczby roboczogodzin niezbędnych do realizacji poszczególnych modułów (Backend: ~120h, Aplikacja Windows: ~150h, Aplikacja Web: ~100h).

Zgodnie z wymogami Regulaminu, zobowiązujemy się do przeprowadzenia formalnego procesu wyboru wykonawcy po podpisaniu umowy inkubacyjnej. W tym celu **przedstawimy co najmniej 3 konkurencyjne oferty** od niezależnych podmiotów, co zapewni transparentność i rynkową wartość realizowanej usługi.
