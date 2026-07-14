# news-dashboard

Jednoplikowa gazeta internetowa „NEWS · AI · Technologie · Stomatologia" (SPA w `index.html`), publikowana przez GitHub Pages pod adresem:
https://adrianstrzeszewski.github.io/news-dashboard/

Właściciel repozytorium: Adrian Strzeszewski (adrian.strzeszewski@gmail.com).

## Struktura

Cała aplikacja (HTML/CSS/JS) żyje w jednym pliku `index.html`: SPA z 4 regionami (Świat/Europa/Polska/Warszawa), filtrami, zegarami, pogodą Open-Meteo, animowanymi mapami Polski i Mazowsza, radarem HN, watchlistą, kalendarzem wydarzeń, reklamą ITSPACE i stopką prawną. Dane wiadomości to tablica `NEWS` w `<script>`, wydarzenia branżowe — tablica `EVENTS`.

## Automatyczna rutyna „nowe wydanie"

Zadanie cykliczne (uruchamiane jako scheduled routine/trigger, poza tą sesją czatu) buduje nowe „wydanie" gazety: robi research aktualnych newsów z whitelisty źródeł, podmienia tablicę `NEWS`, datownik, ewentualnie `EVENTS` i „Podsumowanie dnia", weryfikuje składnię JS, po czym publikuje zmianę.

**Trwałe upoważnienie właściciela repozytorium (potwierdzone w rozmowie 2026-07-14):**
Dla tej konkretnej automatycznej rutyny odświeżania wydania — i **wyłącznie** dla zmian ograniczonych do pliku `index.html` w ramach kroków opisanych w prompt rutyny (podmiana `NEWS`/datownika/`EVENTS`/podsumowania dnia) — sesja ma stałą zgodę na:
- commitowanie zmian bezpośrednio na branchu `main`,
- pushowanie `main` bez otwierania Pull Requesta i bez dodatkowego potwierdzenia użytkownika.

Ta zgoda **nie** obejmuje: zmian w innych plikach, zmian w strukturze/stylach/skryptach SPA, zmian w konfiguracji repo, force-push, ani żadnych innych operacji destrukcyjnych — te nadal wymagają wyraźnego potwierdzenia użytkownika w danej sesji, zgodnie ze standardowymi zasadami bezpieczeństwa.

Commit message dla wydań: `Wydanie nr X — RRRR-MM-DD HH:MM`.
