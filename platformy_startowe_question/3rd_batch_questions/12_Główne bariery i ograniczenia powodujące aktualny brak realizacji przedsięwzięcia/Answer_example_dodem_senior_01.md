Techniczne

• Precyzja detekcji UI

– Różnorodne technologie GUI (Win32, .NET, Electron, HTML/CSS) oraz biblioteki i „skórki” wymagają elastycznego silnika wizualno-strukturalnej analizy okien, stale aktualizowanego algorytmami ML, by utrzymać ≥95% trafności w identyfikacji przycisków, pól tekstowych i menu.

– Dynamiczne UI (SPA, lazy-loading) oznaczają asynchroniczne ładowanie i przesuwanie elementów. Nakładki „dymków” muszą reagować w czasie rzeczywistym, bez opóźnień i błędów pozycjonowania, które obniżałyby UX.

• Pokrycie offline

– Aby zapewnić 70% kluczowych funkcji bez internetu, lokalnie przechowuje się fragmenty „Dodem Memory” (manuale PDF, szablony promptów, modele ML). Ograniczona pojemność dyskowa i RAM na starszych urządzeniach wymusza kompromisy między rozmiarem bazy a funkcjonalnością.

– Szybkie delta-update’y dokumentacji (np. nowa wersja bankowości online) wymagają mechanizmu pobierania tylko zmienionych fragmentów, bez pełnych pakietów, co stanowi istotne wyzwanie inżynieryjne.

Regulacyjne

• RODO i anonimizacja

– Nawet fragmenty UI mogą zawierać PII (e-maile, numery kont), więc konieczna jest analiza DPIA oraz pseudonimizacja/anonimizacja danych przed wysłaniem do chmury. Umowy muszą uwzględniać przetwarzanie jako podwykonawca.

– Jeśli silnik AI działa poza EOG, wymagane są standardowe klauzule umowne (SCC) lub deployment w regionie UE.

Rynkowe

• Budżety UTW i domów kultury

– Ograniczone środki z dotacji i składek: nawet 50-sto stanowiskowy pakiet za 30 000 PLN/rok wymaga decyzji rady programowej i zgody lokalnych urzędów, co wydłuża proces zakupu do kilku kwartałów.

• Przyzwyczajenia seniorów

– Lęk przed instalacją i obawa „zepsucia” systemu wymaga wielokrotnych demonstracji prostoty i bezpieczeństwa.

– Po opanowaniu podstaw mogą porzucić aplikację (wysoki churn).

– Koszt pozyskania seniora (120 PLN przy marketingu offline i online)

Operacyjne

• Dostęp do manuali

– Komercyjne dokumentacje (banki, MS Office) objęte prawami autorskimi wymagają negocjacji licencji na parsowanie i indeksowanie PDF oraz helpów online.

• Koszty licencji LLM

– Modele GPT-4, Anthropic, Google Gemini generują koszty od kilkudziesięciu do kilkuset USD za 1 mln tokenów. Bez throttlingu, batchingu i cache’owania miesięczne rachunki mogą przekroczyć 50 000 PLN. Konieczne są negocjacje rabatów lub część ruchu przeniesiona na tańsze modele open-source.
