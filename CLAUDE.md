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

## Dynamiczny datownik (od 15.07.2026)

Datownik ma dwie części: span #dl-today (dzień, data, imieniny — liczone w przeglądarce czytelnika; NIE wpisuj tam nic) oraz span #dl-edition (statyczna metryka wydania). Przy każdej publikacji aktualizuj WYŁĄCZNIE tekst spanu #dl-edition w formacie „Wydanie nr X · opublikowano D miesiąca RRRR, HH:MM" (czas polski faktycznej publikacji) oraz jego atrybut data-pub w formacie RRRR-MM-DDTHH:MM. NIE zmieniaj spanu #dl-today, tablicy const IMIENINY, funkcji renderToday(), wywołań setInterval ani środkowego segmentu z godzinami aktualizacji. Nie researchuj dnia tygodnia ani imienin — liczy je strona.

## SEO subdomeny (od 15.07.2026)

W <head> index.html są meta SEO (description, canonical na https://news.itspace.com.pl/, Open Graph, Twitter Card) oraz blok JSON-LD — przy przebudowie wydania zachowuj je bez zmian. W repo są pliki robots.txt, llms.txt i sitemap.xml — przy każdej publikacji aktualizuj w sitemap.xml wartość <lastmod> na bieżącą datę (RRRR-MM-DD), pozostałych plików nie zmieniaj.

## Poradniki (od 15.07.2026)

Katalog `poradniki/` (spis `poradniki/index.html` + 15 artykułów `poradniki/<slug>/index.html`) to statyczna sekcja poradnikowa serwowana pod https://news.itspace.com.pl/poradniki/. Rutyna publikacyjna „nowe wydanie" NIE zmienia jej zawartości — nowe artykuły lub modyfikacje istniejących powstają wyłącznie na wyraźne zlecenie właściciela repozytorium. Przy aktualizacji sitemap.xml zachowuj wpisy poradników (spis i artykuły) bez zmian — aktualizuje się tylko <lastmod> strony głównej.
