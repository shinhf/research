### 1. Opis MVP i plan walidacji rynkowej

**Opis MVP (Minimum Viable Product):**
MVP platformy Dodem to aplikacja desktopowa na system Windows, zaprojektowana do szybkiej weryfikacji hipotez biznesowych. Kluczowe funkcje:
*   **Inicjacja pomocy:** Uproszczony mechanizm wzywania wsparcia jednym kliknięciem z zasobnika systemowego.
*   **Sesja zdalna:** Jednokierunkowy streaming ekranu seniora do panelu moderatora, bez możliwości przejęcia kontroli, co gwarantuje bezpieczeństwo.
*   **Podpowiedzi kontekstowe ("dymki"):** Moderator wskazuje element na ekranie seniora, a system (Dodem AI Engine) generuje instrukcję w formie graficznej podpowiedzi ze strzałką, prowadząc użytkownika krok po kroku.
*   **Logowanie zdarzeń:** Zbieranie zanonimizowanych danych (liczba sesji, czas trwania, wskaźnik ukończenia zadań) do analizy użyteczności.

**Plan walidacji rynkowej:**
*   **Grupa pilotażowa:** Testy z udziałem 10-15 seniorów (rekrutowanych we współpracy z UTW) oraz 3-5 moderatorów-wolontariuszy.
*   **Metody zbierania feedbacku:**
    *   **Dane ilościowe:** Automatycznie zbierane metryki, w tym Wskaźnik adopcji (Adoption Rate) i Wskaźnik redukcji błędów (Error Reduction Rate).
    *   **Dane jakościowe:** Ankiety satysfakcji oraz wywiady pogłębione z uczestnikami.
*   **Kryteria sukcesu MVP:**
    *   Wskaźnik adopcji >70% w grupie testowej.
    *   Średnia ocena satysfakcji >4.0 w skali 5-punktowej.
    *   Dokładność podpowiedzi AI >80% (oceniana przez moderatorów).

### 2. Zakres prac własnych i potrzeby w ramach inkubacji

*   **Prace zrealizowane:** Przeprowadzono analizę problemu i rynku, opracowano koncepcję produktu (UVP), stworzono klikalny prototyp w Figmie oraz nawiązano wstępne relacje z partnerami (UTW).
*   **Potrzebne wsparcie w ramach inkubacji:**
    *   **Usługi IT:** Finansowanie prac programistycznych (backend, aplikacja desktopowa dla seniora, panel webowy dla moderatora).
    *   **Wsparcie merytoryczne:** Konsultacje z ekspertami ds. UX/UI dla seniorów, doradztwo prawne (RODO) i w zakresie strategii biznesowej.
    *   **Wsparcie organizacyjne:** Pomoc w rekrutacji i koordynacji grupy pilotażowej.

### 3. Charakterystyka usług finansowanych z grantu

*   **Nazwa usługi:** "Stworzenie oprogramowania MVP dla platformy asystenta cyfrowego Dodem".
*   **Szczegółowy zakres:**
    1.  **Backend:** REST API, system uwierzytelniania, zarządzanie sesjami streamingu, moduł do logowania metryk.
    2.  **Aplikacja desktopowa (Senior):** UI, implementacja jednokierunkowego streamingu pulpitu i warstwy do wyświetlania "dymków".
    3.  **Aplikacja webowa (Moderator):** Interfejs do podglądu streamu, narzędzia do wysyłania "dymków", panel weryfikacji sugestii AI.
*   **Czas realizacji:** 4 miesiące.

### 4. Uzasadnienie szacowanego kosztu usługi

Koszt oszacowano na podstawie analizy rynku usług programistycznych, wstępnych konsultacji z potencjalnymi wykonawcami oraz kalkulacji bazującej na uśrednionych stawkach rynkowych (150-200 PLN netto/h) i szacowanej liczbie roboczogodzin (Backend: ~120h, Aplikacja Windows: ~150h, Aplikacja Web: ~100h). Zgodnie z Regulaminem, po podpisaniu umowy inkubacyjnej zobowiązujemy się do przedstawienia co najmniej 3 konkurencyjnych ofert w celu wyboru wykonawcy.
