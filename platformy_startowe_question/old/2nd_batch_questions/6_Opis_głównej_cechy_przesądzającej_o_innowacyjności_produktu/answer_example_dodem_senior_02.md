Silnik kontekstowego prowadzenia na ekranie z deterministycznym zakotwiczeniem w elementach UI

To jedna, decydująca przewaga Dodem. System w czasie rzeczywistym rozpoznaje strukturę interfejsu i stan zadania, a następnie przypina podpowiedź dokładnie do właściwego elementu UI w dowolnej aplikacji na Windows i macOS oraz w przeglądarce. Nie wymaga ręcznego authoringuflow jak klasyczne DAP i nie działa wyłącznie tekstem jak chatboty.

Jak to działa

Analiza kontekstu: detekcja okna, kontrolki, fokusu, zmian rozmiaru i przewijania.

Zakotwiczenie: overlay przypięty do konkretnego elementu UI, odporny na ruch okna i zmianę layoutu.

Generowanie instrukcji: RAG z kuratowanej bazy Dodem Memory oraz szablony zadaniowe, LLM tylko do uproszczenia języka i dopasowania do kroku.

Polityki jakości: walidacja treści, de-duplikacja kroków, kontrola długości, prosty rejestr błędów do retrainingu.

Prywatność: lokalne maskowanie PII, brak logowania haseł, szyfrowanie w transmisji i spoczynku, minimalna retencja.

Tryb offline: cache najczęstszych scenariuszy zapewnia działanie bez internetu.

Dlaczego to przełom

Działa poza przeglądarką i bez vendor lock-in aplikacji.

Skaluje się ekonomicznie dzięki automatycznej ekstrakcji wiedzy z manuali i tutoriali do Dodem Memory, zamiast ręcznego budowania ścieżek.

Zapewnia mierzalną przewidywalność działania w realnych czynnościach seniora.

Twarde parametry

Czas dostarczenia podpowiedzi do 1,5 s.

Trafność instrukcji co najmniej 95 proc.

Pokrycie trybem offline co najmniej 70 proc. kluczowych funkcji.

Dostępność usług 99,9 proc.

Docelowo redukcja błędów użytkownika o 60 proc. i skrócenie czasu wykonania typowych czynności o 40 proc.

Kontrast do alternatyw

Klasyczne DAP: głównie web, wysoki nakład ręcznego authoringu, niska przydatność w scenariuszach konsumenckich 60 plus.

Chatboty LLM: brak natywnego kontekstu ekranu i brak precyzyjnego pozycjonowania wskazówek w UI.

Jedna cecha, która to wszystko spina: prowadzenie na ekranie osadzone w interfejsie użytkownika, a nie obok niego.
