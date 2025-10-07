11.1 Obecnypoziom TRL: TRL 3 – Proof of Concept

• Działająca aplikacja desktopowa Windows z podstawowym mechanizmem „dymków” i prototypowym silnikiem AI

• „Dodem Memory” zaimplementowane jako lokalne repozytorium dokumentów i ręcznie weryfikowanych instrukcji

• Architektura systemu opracowana w skali makro (klient, chmura, AI), brak jeszcze pełnej optymalizacji latency i bezpieczeństwa

• Moduł anonimizacji danych i end-to-end szyfrowanie wstępnie zintegrowane, ale niezweryfikowane w warunkach rzeczywistych

11.2 Kluczowe kroki do osiągnięcia TRL 9

• TRL 4 – Laboratoryjna walidacja komponentów

– Udoskonalenie silnika AI: wdrożenie prompt-engineering i caching odpowiedzi, redukcja TTI do ≤1,5 s

– Integracja lokalnego modelu offline i testy wydajnościowe na maszynach docelowych

– Automatyczne testy anonimizacji i szyfrowania danych

• TRL 5 – Walidacja w środowisku symulowanym

– Testy end-to-end z udziałem 10–20 użytkowników-seniorów w kontrolowanych warunkach labo¬ratoryjnych

– Pomiar KPI (TTI, trafność podpowiedzi, coverage offline) i iteracje UX/UI pod kątem WCAG

• TRL 6 – Demonstracja w warunkach rzeczywistych (pilotaż)

– Pilotaż w 2–3 ośrodkach UTW (50–100 seniorów) przez min. 4 tygodnie

– Zbieranie metryk użycia, błędów, feedbacku i adaptacja architektury chmurowej pod obciążenie

• TRL 7 – System demonstracyjny w środowisku operacyjnym

– Rozszerzenie pilotażu o partnerstwo z oddziałami banku

– Certyfikacja zgodności RODO, audyt bezpieczeństwa (penetrationtesting)

– Wstępne przygotowanie dokumentacji operacyjnej i materiałów szkoleniowych dla helpdesku

• TRL 8 – Kompletny system weryfikowany

– Ukończenie integracji wieloplatformowej (macOS, iOS, Android)

– Ustanowienie procesu CI/CD, SLA 99,9%, monitoring produkcyjny i DisasterRecovery

– Szkolenia partnerów, finalizacja programów onboardingowych (UTW, domy kultury, banki)

• TRL 9 – System sprawdzony w docelowym środowisku

– Komercyjna premiera produktu, pełne wsparcie B2C i B2B2C, osiągnięcie celu 5 000 – 10 000 płacących użytkowników

– Skalowanie infrastruktury, utrzymanie SLA, ciągła aktualizacja „Dodem Memory” i modeli AI

– Budowa wewnętrznego Działu Obsługi Klienta i CustomerSuccess, monitoring LTV/CAC/CSAT
