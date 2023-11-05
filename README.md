# Baza-Projekt

-- phpMyAdmin SQL Dump
-- version 5.1.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Czas generowania: 05 Lis 2023, 19:04
-- Wersja serwera: 10.4.22-MariaDB
-- Wersja PHP: 8.1.1

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Baza danych: `bazaprojekt`
--

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `aplikacjeużytkownika`
--

CREATE TABLE `aplikacjeużytkownika` (
  `Aplikacja_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `ogłoszenie_id` int(11) DEFAULT NULL,
  `DataAplikacji` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `doświadczenie`
--

CREATE TABLE `doświadczenie` (
  `Doświadczenie_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `Stanowisko` varchar(100) DEFAULT NULL,
  `NazwaFirmy` varchar(100) DEFAULT NULL,
  `Lokalizacja` varchar(100) DEFAULT NULL,
  `OkresZatrudnienia` varchar(100) DEFAULT NULL,
  `Obowiązki` text DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `firmy`
--

CREATE TABLE `firmy` (
  `Firma_id` int(11) NOT NULL,
  `NazwaFirmy` varchar(100) DEFAULT NULL,
  `AdresFirmy` varchar(200) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `języki`
--

CREATE TABLE `języki` (
  `Język_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `NazwaJęzyka` varchar(50) DEFAULT NULL,
  `PoziomZnajomości` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `kontafirm`
--

CREATE TABLE `kontafirm` (
  `KontoFirmy_id` int(11) NOT NULL,
  `Firma_id` int(11) DEFAULT NULL,
  `NazwaUżytkownika` varchar(50) DEFAULT NULL,
  `Hasło` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `kursy`
--

CREATE TABLE `kursy` (
  `Kurs_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `NazwaKursu` varchar(100) DEFAULT NULL,
  `Organizator` varchar(100) DEFAULT NULL,
  `DataKursu` date DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `ogłoszeniapracy`
--

CREATE TABLE `ogłoszeniapracy` (
  `ogłoszenie_id` int(11) NOT NULL,
  `Firma_id` int(11) DEFAULT NULL,
  `NazwaStanowiska` varchar(100) DEFAULT NULL,
  `PoziomZatrudnienia` varchar(50) DEFAULT NULL,
  `RodzajUmowy` varchar(50) DEFAULT NULL,
  `RodzajPracy` varchar(50) DEFAULT NULL,
  `PracaZdalna` tinyint(1) DEFAULT NULL,
  `WidełkiWynagrodzenia` varchar(50) DEFAULT NULL,
  `DniPracy` varchar(50) DEFAULT NULL,
  `GodzinyPracy` varchar(50) DEFAULT NULL,
  `DataWygaśnięcia` date DEFAULT NULL,
  `Kategoria` varchar(50) DEFAULT NULL,
  `OpisStanowiska` text DEFAULT NULL,
  `Wymagania` text DEFAULT NULL,
  `Oferty` text DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `ulubioneogłoszeniaużytkownika`
--

CREATE TABLE `ulubioneogłoszeniaużytkownika` (
  `UlubioneOgłoszenie_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `ogłoszenie_id` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `umiejętności`
--

CREATE TABLE `umiejętności` (
  `Umiejętność_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `NazwaUmiejętności` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `użytkownicy`
--

CREATE TABLE `użytkownicy` (
  `Użytkownik_id` int(11) NOT NULL,
  `Imię` varchar(50) DEFAULT NULL,
  `Nazwisko` varchar(50) DEFAULT NULL,
  `DataUrodzenia` date DEFAULT NULL,
  `Email` varchar(100) DEFAULT NULL,
  `NumerTelefonu` varchar(15) DEFAULT NULL,
  `ZdjęcieProfilowe` blob DEFAULT NULL,
  `Adres` varchar(200) DEFAULT NULL,
  `AktualneStanowiskoPracy` varchar(100) DEFAULT NULL,
  `OpisStanowiskaPracy` text DEFAULT NULL,
  `PodsumowanieZawodowe` text DEFAULT NULL,
  `LinkedInProfil` varchar(100) DEFAULT NULL,
  `GitHubProfil` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Struktura tabeli dla tabeli `wykształcenie`
--

CREATE TABLE `wykształcenie` (
  `Wykształcenie_id` int(11) NOT NULL,
  `Użytkownik_id` int(11) DEFAULT NULL,
  `NazwaSzkolyUczelni` varchar(100) DEFAULT NULL,
  `Lokalizacja` varchar(100) DEFAULT NULL,
  `PoziomWykształcenia` varchar(50) DEFAULT NULL,
  `Kierunek` varchar(100) DEFAULT NULL,
  `Okres` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Indeksy dla zrzutów tabel
--

--
-- Indeksy dla tabeli `aplikacjeużytkownika`
--
ALTER TABLE `aplikacjeużytkownika`
  ADD PRIMARY KEY (`Aplikacja_id`),
  ADD KEY `Użytkownik_id` (`Użytkownik_id`),
  ADD KEY `ogłoszenie_id` (`ogłoszenie_id`);

--
-- Indeksy dla tabeli `doświadczenie`
--
ALTER TABLE `doświadczenie`
  ADD PRIMARY KEY (`Doświadczenie_id`),
  ADD KEY `IDUżytkownika` (`Użytkownik_id`);

--
-- Indeksy dla tabeli `firmy`
--
ALTER TABLE `firmy`
  ADD PRIMARY KEY (`Firma_id`);

--
-- Indeksy dla tabeli `języki`
--
ALTER TABLE `języki`
  ADD PRIMARY KEY (`Język_id`),
  ADD KEY `IDUżytkownika` (`Użytkownik_id`);

--
-- Indeksy dla tabeli `kontafirm`
--
ALTER TABLE `kontafirm`
  ADD PRIMARY KEY (`KontoFirmy_id`);

--
-- Indeksy dla tabeli `kursy`
--
ALTER TABLE `kursy`
  ADD PRIMARY KEY (`Kurs_id`),
  ADD KEY `IDUżytkownika` (`Użytkownik_id`);

--
-- Indeksy dla tabeli `ogłoszeniapracy`
--
ALTER TABLE `ogłoszeniapracy`
  ADD PRIMARY KEY (`ogłoszenie_id`),
  ADD KEY `Firma_id` (`Firma_id`);

--
-- Indeksy dla tabeli `ulubioneogłoszeniaużytkownika`
--
ALTER TABLE `ulubioneogłoszeniaużytkownika`
  ADD PRIMARY KEY (`UlubioneOgłoszenie_id`),
  ADD KEY `Użytkownik_id` (`Użytkownik_id`),
  ADD KEY `ogłoszenie_id` (`ogłoszenie_id`);

--
-- Indeksy dla tabeli `umiejętności`
--
ALTER TABLE `umiejętności`
  ADD PRIMARY KEY (`Umiejętność_id`),
  ADD KEY `IDUżytkownika` (`Użytkownik_id`);

--
-- Indeksy dla tabeli `użytkownicy`
--
ALTER TABLE `użytkownicy`
  ADD PRIMARY KEY (`Użytkownik_id`);

--
-- Indeksy dla tabeli `wykształcenie`
--
ALTER TABLE `wykształcenie`
  ADD PRIMARY KEY (`Wykształcenie_id`),
  ADD KEY `IDUżytkownika` (`Użytkownik_id`);

--
-- AUTO_INCREMENT dla zrzuconych tabel
--

--
-- AUTO_INCREMENT dla tabeli `aplikacjeużytkownika`
--
ALTER TABLE `aplikacjeużytkownika`
  MODIFY `Aplikacja_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `doświadczenie`
--
ALTER TABLE `doświadczenie`
  MODIFY `Doświadczenie_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `firmy`
--
ALTER TABLE `firmy`
  MODIFY `Firma_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `języki`
--
ALTER TABLE `języki`
  MODIFY `Język_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `kontafirm`
--
ALTER TABLE `kontafirm`
  MODIFY `KontoFirmy_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `kursy`
--
ALTER TABLE `kursy`
  MODIFY `Kurs_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `ogłoszeniapracy`
--
ALTER TABLE `ogłoszeniapracy`
  MODIFY `ogłoszenie_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `ulubioneogłoszeniaużytkownika`
--
ALTER TABLE `ulubioneogłoszeniaużytkownika`
  MODIFY `UlubioneOgłoszenie_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `umiejętności`
--
ALTER TABLE `umiejętności`
  MODIFY `Umiejętność_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `użytkownicy`
--
ALTER TABLE `użytkownicy`
  MODIFY `Użytkownik_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT dla tabeli `wykształcenie`
--
ALTER TABLE `wykształcenie`
  MODIFY `Wykształcenie_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- Ograniczenia dla zrzutów tabel
--

--
-- Ograniczenia dla tabeli `aplikacjeużytkownika`
--
ALTER TABLE `aplikacjeużytkownika`
  ADD CONSTRAINT `aplikacjeużytkownika_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`),
  ADD CONSTRAINT `aplikacjeużytkownika_ibfk_2` FOREIGN KEY (`ogłoszenie_id`) REFERENCES `ogłoszeniapracy` (`ogłoszenie_id`);

--
-- Ograniczenia dla tabeli `doświadczenie`
--
ALTER TABLE `doświadczenie`
  ADD CONSTRAINT `doświadczenie_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`);

--
-- Ograniczenia dla tabeli `języki`
--
ALTER TABLE `języki`
  ADD CONSTRAINT `języki_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`);

--
-- Ograniczenia dla tabeli `kursy`
--
ALTER TABLE `kursy`
  ADD CONSTRAINT `kursy_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`);

--
-- Ograniczenia dla tabeli `ogłoszeniapracy`
--
ALTER TABLE `ogłoszeniapracy`
  ADD CONSTRAINT `ogłoszeniapracy_ibfk_1` FOREIGN KEY (`Firma_id`) REFERENCES `firmy` (`Firma_id`);

--
-- Ograniczenia dla tabeli `ulubioneogłoszeniaużytkownika`
--
ALTER TABLE `ulubioneogłoszeniaużytkownika`
  ADD CONSTRAINT `ulubioneogłoszeniaużytkownika_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`),
  ADD CONSTRAINT `ulubioneogłoszeniaużytkownika_ibfk_2` FOREIGN KEY (`ogłoszenie_id`) REFERENCES `ogłoszeniapracy` (`ogłoszenie_id`);

--
-- Ograniczenia dla tabeli `umiejętności`
--
ALTER TABLE `umiejętności`
  ADD CONSTRAINT `umiejętności_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`);

--
-- Ograniczenia dla tabeli `wykształcenie`
--
ALTER TABLE `wykształcenie`
  ADD CONSTRAINT `wykształcenie_ibfk_1` FOREIGN KEY (`Użytkownik_id`) REFERENCES `użytkownicy` (`Użytkownik_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
