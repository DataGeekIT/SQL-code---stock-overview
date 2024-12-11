## 1. WITH ExchangeRates AS
Tworzy tymczasową tabelę ExchangeRates, która oblicza kursy wymiany walut na podstawie tabeli ttcmcs0081000. Kursy wymiany są wyliczane w zależności od tego, czy kurs jest mniejszy niż 1, czy większy (w zależności od wartości t_rate i t_ratf).

## 2. WITH PlannedDemand AS
Tworzy tabelę PlannedDemand, która sumuje zapotrzebowanie (t_qana) dla produktów w magazynach (t_cwar), gdzie t_plnc = '001'. Zapotrzebowanie jest grupowane według magazynu i identyfikatora artykułu.

## 3. WITH LastConsumptionDate AS
Tworzy tabelę LastConsumptionDate, która zwraca datę ostatniego zużycia dla każdego artykułu (t_item) w każdym magazynie (t_cwar), bazując na tabeli twhinr1101000, filtrując po typie transakcji (np. t_koor = '1' i t_kost = '5').

## 4. WITH LastSalesDate AS
Tworzy tabelę LastSalesDate, która zwraca datę ostatniej sprzedaży dla artykułów w magazynach na podstawie transakcji sprzedaży w tabeli twhinr1101000, łącząc ją z tabelą twhinh2001000 (zawierającą dane o zamówieniach).

## 5. WITH LastReceiptDate AS
Tworzy tabelę LastReceiptDate, która zwraca datę ostatniego przyjęcia towaru w magazynie, bazując na transakcjach zakupu w tabeli twhinr1101000, łącząc ją z tabelą twhinh2001000.

## 6. SELECT (Właściwa część zapytania)
Główne zapytanie pobiera szczegóły dotyczące artykułów, ich zapasów, wartości i powiązanych danych w następujących kolumnach:

Enterprise Unit (Jednostka przedsiębiorstwa) — modyfikacja identyfikatora jednostki w zależności od wartości t_comp.

Warehouse (Magazyn) — identyfikator magazynu.

Warehouse Name (Nazwa magazynu) — nazwa magazynu.

Warehouse Type (Typ magazynu) — określa, czy magazyn jest własnością klienta, czy firmy.

Owner (Właściciel) — kategoria właściciela magazynu (np. Operacje, Sprzedaż, Serwis).

Responsible Person (Odpowiedzialna osoba) — osoba odpowiedzialna za magazyn.

ItemID (Identyfikator artykułu) — identyfikator artykułu.

Item Description (Opis artykułu) — opis artykułu.

Signal (Sygnalizacja) — kod sygnalizacyjny artykułu.

Signal Description (Opis sygnalizacji) — opis sygnalizacyjny.

Product Class, Item Group, Product Line — klasyfikacja artykułów, grupy, i linie produktów.

Standard Cost (Koszt standardowy) — koszt standardowy artykułu.

Std Cost Currency (Waluta kosztu standardowego) — waluta kosztu.

Std Cost USD PEG (Koszt standardowy w USD PEG) — koszt w przeliczeniu na USD przy uwzględnieniu kursów wymiany.

Inventory Unit (Jednostka inwentarza) — jednostka miary artykułu w inwentarzu.

On Hand Q-ty with customer (Ilość na stanie u klienta) — ilość artykułu przechowywaną u klienta.

Customer Owned QTY (Ilość własności klienta) — ilość artykułu będąca własnością klienta.

On Hand QTY (Ilość na stanie) — ilość artykułu w magazynie (na stanie).

Stock Value in Std Cost USD PEG (Wartość zapasu w standardowym koszcie USD PEG) — wartość zapasu w magazynie przeliczona na USD przy użyciu kursów wymiany.

Planned Demand (Zapotrzebowanie planowane) — zapotrzebowanie na artykuł z planowania.

Last consumption date (Ostatnia data zużycia) — data ostatniego zużycia artykułu.

Last sales date (Ostatnia data sprzedaży) — data ostatniej sprzedaży artykułu.

Last receipt date (Ostatnia data przyjęcia) — data ostatniego przyjęcia artykułu do magazynu.

Last Movement Date ANY (Data ostatniego ruchu) — data ostatniego ruchu artykułu w systemie.

Safety Stock (Zapas bezpieczeństwa) — zapas artykułu przeznaczony na bezpieczeństwo.


## 7. JOIN
W zapytaniu są wykonane liczne połączenia (JOIN) z różnymi tabelami, aby uzyskać wszystkie wymagane dane:

Erplndb.dbo.twhwmd2151000 — główna tabela z danymi o artykułach w magazynach.

Erplndb.dbo.1, Erplndb.dbo.2, Erplndb.dbo.3 — różne tabele z danymi o firmach, osobach odpowiedzialnych, i opisach artykułów.

Erplndb.dbo.4, Erplndb.dbo.5, Erplndb.dbo.6 — tabele z dodatkowymi informacjami o artykułach, kosztach, i zapotrzebowaniu.

Erplndb.dbo.7 — tabela z zapasami bezpieczeństwa.

## 8. WHERE item.t_qhnd > 0
Na końcu zapytania filtruje artykuły, które mają ilość większą niż 0 w magazynie.
