#  CommunityHub — Dokumentacja Systemu

**CommunityHub** to zdecentralizowana platforma mikroblogowa, która priorytetyzuje wolność słowa, niszowe zainteresowania i kontrolę użytkownika nad algorytmem. Projekt łączy dynamikę serwisu X z funkcjonalnością forum tematycznego.

---

##  Kluczowe Funkcjonalności

### 1. Huby (Serce Platformy)
Zamiast jednego, ogólnego feedu, użytkownicy mogą tworzyć i dołączać do **Hubów**:
* **Huby Tematyczne:** Np. `/h/technologia`, `/h/kuchnia`, `/h/gaming`.
* **Własne Zasady:** Każdy Hub posiada unikalny regulamin ustalany przez założyciela.
* **Rangi:** Aktywni członkowie zdobywają punkty reputacji wewnątrz konkretnego Huba.

### 2. Mikroblogowanie (The Pulse)
* **Hub-Posty:** Krótkie formy do 320 znaków.
* **Media:** Obsługa galerii zdjęć (do 10), wideo 4K oraz ankiet interaktywnych.
* **Markdown Support:** Podstawowa składnia Markdown wewnątrz postów (pogrubienia, linki, listy).

### 3. Mechanika Interakcji
| Nazwa | Akcja | Skutek |
| :--- | :--- | :--- |
| **Spark** | *Polubienie* | Zwiększa widoczność posta w danym Hubie. |
| **Echo** | *Udostępnienie* | Przesyła post do obserwujących Twojego profilu. |
| **Quote** | *Cytat* | Pozwala na dodanie komentarza do czyjegoś posta. |
| **Whisper** | *DM* | Prywatna, szyfrowana (E2EE) komunikacja między użytkownikami. |

---

##  Architektura Systemu

### Frontend
* **Framework:** Next.js 14+ (App Router).
* **Stylizacja:** Tailwind CSS z systemem motywów (Light/Dark/OLED).
* **State Management:** Zustand / TanStack Query.

### Backend & Data
* **API:** GraphQL dla elastycznego pobierania danych o postach.
* **Real-time:** WebSockets (Socket.io) dla powiadomień i czatów na żywo.
* **Bazy danych:** * *PostgreSQL:* Dane użytkowników i posty.
    * *Redis:* Cache, sesje i rankingi trendów.
    * *S3 Bucket:* Przechowywanie multimediów.

---

##  Model Biznesowy i Monetyzacja

Model oparty na transparentności, a nie handlu danymi:
* **CommunityHub+:** Opcjonalna subskrypcja (większe pliki, unikalne odznaki, brak reklam od sponsorów).
* **Promowane Huby:** Możliwość reklamy całych społeczności, a nie pojedynczych produktów.
* **Marketplace:** Miejsce dla twórców na sprzedaż treści cyfrowych (np. presety, kursy).

---

##  Roadmap Projektu

### Faza 1: Fundamenty (Q2 2026)
- [x] System publikacji postów i podstawowych interakcji.
- [x] Uruchomienie modułu Hubów.
- [x] System monetyzacji dla twórców.

