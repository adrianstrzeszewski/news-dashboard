# news-dashboard

Jednoplikowa strona „NEWS · AI · Technologie · Stomatologia" (SPA w `index.html`), publikowana przez GitHub Pages pod adresem https://news.itspace.com.pl/.

Właściciel repozytorium: Adrian Strzeszewski (adrian.strzeszewski@gmail.com).

## Struktura

Cała strona (HTML/CSS/JS) żyje w jednym pliku `index.html`: 4 regiony (Świat/Europa/Polska/Warszawa), filtry, zegary, pogoda (Open-Meteo), mapy, radar HN, watchlista, kalendarz wydarzeń, blok ITSPACE i stopka. Treść wiadomości to tablica `NEWS` w `<script>`, wydarzenia branżowe — tablica `EVENTS`.

## Zasady aktualizacji treści (index.html)

Aktualizacja „wydania" ogranicza się do zawartości: tablica `NEWS`, datownik `#dl-edition`, ewentualnie `EVENTS` i „Podsumowanie dnia"; następnie weryfikacja składni JS. NIE zmieniaj struktury, stylów, skryptów SPA ani innych plików.

Upoważnienie właściciela (2026-07-14): zmiany ograniczone WYŁĄCZNIE do powyższej aktualizacji treści w `index.html` mogą być commitowane i pushowane na `main` bez Pull Requesta i bez dodatkowego potwierdzenia. Każda inna zmiana (inne pliki, struktura/style/skrypty, konfiguracja repo, force-push, operacje destrukcyjne) wymaga wyraźnego potwierdzenia użytkownika w danej sesji.

Format commita wydań: `Wydanie nr X — RRRR-MM-DD HH:MM`.

## Datownik

Datownik ma dwie części: `#dl-today` (dzień, data, imieniny — liczone w przeglądarce; NIE wpisuj tam nic i nie zmieniaj `const IMIENINY`, `renderToday()`, `setInterval` ani segmentu godzin) oraz `#dl-edition` (statyczna metryka wydania). Aktualizuj WYŁĄCZNIE tekst `#dl-edition` w formacie „Wydanie nr X · opublikowano D miesiąca RRRR, HH:MM" oraz atrybut `data-pub` w formacie RRRR-MM-DDTHH:MM.

## SEO

W `<head>` są meta (description, canonical, Open Graph, Twitter Card) oraz blok JSON-LD — zachowuj bez zmian. Pliki `robots.txt`, `llms.txt`, `sitemap.xml` — przy publikacji aktualizuj wyłącznie `<lastmod>` strony głównej w `sitemap.xml` na bieżącą datę (RRRR-MM-DD); pozostałych wpisów i plików nie zmieniaj.

## Poradniki

Katalog `poradniki/` (spis `poradniki/index.html` + artykuły `poradniki/<slug>/index.html`) serwowany pod /poradniki/. Aktualizacja wydania NIE zmienia jego zawartości — nowe artykuły lub modyfikacje powstają wyłącznie na wyraźne zlecenie właściciela. Wpisy poradników w `sitemap.xml` zostają bez zmian.

## Statystyki odwiedzin

Tuż przed `</body>` w `index.html` i na każdej stronie w `poradniki/` jest fragment „Cloudflare Web Analytics" (skrypt `beacon.min.js` z tokenem witryny news.itspace.com.pl). Zachowuj go bez zmian przy każdej aktualizacji wydania — bez niego statystyki przestają się liczyć. Token jest jawny (identyfikuje witrynę, nie daje dostępu do konta). Stopka gazety informuje czytelników o tych statystykach; nie usuwaj tego zdania.
