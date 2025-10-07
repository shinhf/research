1) Kontekstowe prowadzenie na ekranie z pewnym zakotwiczeniem w UI
   Podpowiedzi są przypinane deterministycznie do konkretnych elementów interfejsu w aplikacjach desktopowych i w przeglądarce. Stabilność pozycjonowania zachowana przy zmianie rozmiaru okna, przewijaniu i przełączaniu kart.
2) Wielośrodowiskowość bez integracji po stronie dostawców
   Działa w Windows i macOS, zarówno w aplikacjach natywnych, jak i webowych. Brak vendor lock-in i brak konieczności wdrożeń po stronie banku, ZUS czy poczty. Czas uruchomienia nowej aplikacji: od godzin do 2–3 dni (bez tygodniowego authoringu).
3) Dodem Memory (RAG na anej wiedzy)
   Automatyczne pozyskiwanie instrukcji z oficjalnych manuali, PDF i transkryptów wideo. Reguły walidacji eliminują błędy generatywne. Aktualizacja domeny wiedzy bez publikowania nowej wersji klienta.
4) Silnik instrukcji zadaniowych
   LLM używany do skracania i upraszczania języka oraz dopasowania do bieżącego kroku. Instrukcje są zwięzłe, jednokrokowe, z jasnym “co” i “gdzie”. Target: TTI do 1,5 s, trafność ≥ 95 proc.
5) Tryb offline i przetwarzanie przy brzegu
   Pamięć podręczna najczęstszych scenariuszy pozwala działać bez internetu. Cel: pokrycie offline ≥ 70 proc. kluczowych zadań (logowanie, odczyt korespondencji, podstawowe płatności).
6) Privacy by design
   Lokalne maskowanie danych wrażliwych, brak logowania haseł, szyfrowanie w transmisji i w spoczynku, minimalna retencja. Pełna kontrola użytkownika i opiekuna nad telemetrią.
7) Dostępność zaprojektowana pod 60+
   Duże kroje pisma i hitboxy, wysoki kontrast, narracja TTS, proste słownictwo i jednoznaczne komunikaty. Zgodność z WCAG w praktyce, nie tylko w dokumentacji.
8) Szyny bezpieczeństwa akcji
   Podpowiedzi nie wykonują operacji zamiast użytkownika. Dodatkowe potwierdzenia przy krokach ryzykownych (np. kwota przelewu), blokady na skróty prowadzące do błędów.
9) Opiekun rodzinny i pakiet Family
   Zdalne wstępne ustawienia i profile, współdzielenie scenariuszy i szybkie przywracanie konfiguracji na wielu urządzeniach bez wglądu w treść haseł.
10) Mierzalność i automatyczna kontrola jakości
    KPI produktowe i operacyjne: TTI, trafność, CSAT, SLA 99,9 proc. z automatycznym wycofaniem wadliwych wskazówek i retrainingiem. Cele efektowe: redukcja błędów o 60 proc., skrócenie czasu wykonania typowych czynności o 40 proc.
11) Zero-authoring w porównaniu z klasycznymi DAP
    Brak ręcznego budowania ścieżek dla każdej aplikacji. Pokrycie nowych domen wiedzy osiągane przez zasilenie Dodem Memory i automatyczne dopasowanie do elementów UI. Koszt krańcowy wdrażania kolejnych aplikacji drastycznie niższy.
12) Skalowalna dystrybucja i utrzymanie
    Aktualizacje wiedzy po stronie chmury bez dotykania klienta. Rollout partiami, A/B testy wskazówek, telemetria jakości. Gotowe do replikacji w wielu krajach z lokalizacją treści.
