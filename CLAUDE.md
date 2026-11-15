# news-dashboard

Jednoplikowa strona „NEWS · AI · Technologie · Stomatologia" (SPA w `index.html`), publikowana przez GitHub Pages pod adresem https://news.itspace.com.pl/.

Właściciel repozytorium: Adrian Strzeszewski (adrian.strzeszewski@gmail.com).

## Struktura

Cała strona (HTML/CSS/JS) żyje w jednym pliku `index.html`: 4 regiony (Świat/Europa/Polska/Warszawa), filtry, zegary, pogoda (Open-Meteo: kafelki w nagłówku regionu i wykres temperatur na 7 dni; animowane mapy pogodowe usunięto 2026-11-15), radar HN, watchlista, kalendarz wydarzeń, blok ITSPACE i stopka. Treść wiadomości to tablica `NEWS` w `<script>`, wydarzenia branżowe — tablica `EVENTS`.

## Zasady aktualizacji treści (index.html)

Aktualizacja „wydania" ogranicza się do zawartości: tablica `NEWS`, datownik `#dl-edition`, ewentualnie `EVENTS` i „Podsumowanie dnia"; następnie weryfikacja składni JS. NIE zmieniaj struktury, stylów, skryptów SPA ani innych plików (jedyny wyjątek: `<lastmod>` strony głównej w `sitemap.xml`, patrz SEO).

„Podsumowanie dnia" (`#day-summary`) ma dokładnie 10 zwięzłych pozycji (tytuł + jedno zdanie + źródło). Każda pozycja powstaje z jednego wpisu tablicy `NEWS` po jego weryfikacji i nie zawiera niczego, czego w tym wpisie nie ma; miejsca 8–10 są dla kategorii AI, Tech i Stomatologia. Szczegóły doboru i kontrola mechaniczna: prompt rutyny publikującej, KROK 4C.

Upoważnienie właściciela (2026-07-14, rozszerzone 2026-11-15 o `sitemap.xml`): zmiany ograniczone WYŁĄCZNIE do powyższej aktualizacji treści w `index.html` oraz `<lastmod>` strony głównej w `sitemap.xml` mogą być commitowane i pushowane na `main` bez Pull Requesta i bez dodatkowego potwierdzenia. Każda inna zmiana (inne pliki, struktura/style/skrypty, konfiguracja repo, force-push, operacje destrukcyjne) wymaga wyraźnego potwierdzenia użytkownika w danej sesji.

Format commita wydań: `Wydanie nr X — RRRR-MM-DD HH:MM`.

## Datownik

Datownik ma dwie części: `#dl-today` (dzień, data, imieniny — liczone w przeglądarce; NIE wpisuj tam nic i nie zmieniaj `const IMIENINY`, `renderToday()`, `setInterval` ani segmentu godzin) oraz `#dl-edition` (statyczna metryka wydania). Aktualizuj WYŁĄCZNIE tekst `#dl-edition` w formacie „Wydanie nr X · opublikowano D miesiąca RRRR, HH:MM" oraz atrybut `data-pub` w formacie RRRR-MM-DDTHH:MM.

Godzina wydania pochodzi z zegara, nie z szacunku: `TZ=Europe/Warsaw date '+%Y-%m-%dT%H:%M'` tuż przed commitem (czas warszawski, sam uwzględnia czas letni i zimowy). Ta sama wartość trafia do tekstu `#dl-edition`, do `data-pub` i do komunikatu commita. Strona przelicza `data-pub` na czas bezwzględny z przesunięciem właściwym dla tej daty (CET/CEST) — nie wpisuj przesunięcia na sztywno.

## SEO

W `<head>` są meta (description, canonical, Open Graph, Twitter Card) oraz blok JSON-LD — zachowuj bez zmian. Pliki `robots.txt`, `llms.txt`, `sitemap.xml` — przy publikacji aktualizuj wyłącznie `<lastmod>` strony głównej w `sitemap.xml` na bieżącą datę (RRRR-MM-DD); pozostałych wpisów i plików nie zmieniaj.

## Poradniki

Katalog `poradniki/` (spis `poradniki/index.html` + artykuły `poradniki/<slug>/index.html`) serwowany pod /poradniki/. Aktualizacja wydania NIE zmienia jego zawartości — nowe artykuły lub modyfikacje powstają wyłącznie na wyraźne zlecenie właściciela. Wpisy poradników w `sitemap.xml` zostają bez zmian.

## Statystyki odwiedzin

Tuż przed `</body>` w `index.html` i na każdej stronie w `poradniki/` jest fragment „Cloudflare Web Analytics" (skrypt `beacon.min.js` z tokenem witryny news.itspace.com.pl). Zachowuj go bez zmian przy każdej aktualizacji wydania — bez niego statystyki przestają się liczyć. Token jest jawny (identyfikuje witrynę, nie daje dostępu do konta). Stopka gazety informuje czytelników o tych statystykach; nie usuwaj tego zdania.

## Film i strona „Jak powstaje wydanie”

- `redakcja.html` (adres /redakcja) to osobna, stała strona o procesie redakcyjnym: film, animowana hala i opis etapów. Liczby czyta sama z bieżącego `index.html`. Aktualizacja wydania jej NIE zmienia.
- `jak-powstaje-wydanie.mp4` i `jak-powstaje-wydanie.jpg` (katalog główny) to film i jego miniatura. Nie usuwaj i nie podmieniaj ich przy wydaniu.
- W `index.html`, zaraz pod sekcją `#day-summary`, jest karta `<section id="film-card">` oraz jej skrypt na końcu głównego `<script>` (blok „karta z filmem”). To stały element strony, nie część wydania: zachowuj go bez zmian, razem z linkami w stopce (`#film-show` i link do `redakcja.html`). Czytelnik może kartę ukryć; wybór zapisuje jego przeglądarka (localStorage, bez cookies).
- Wpis `/redakcja` w `sitemap.xml` zostaje bez zmian przy publikacji wydania.

