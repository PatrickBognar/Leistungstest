# Leistungstest
Zum Testen der SQL Datenbank
Dieses Skript führt einen TPC-C-Benchmark auf einem Microsoft SQL Server durch. Der TPC-C-Benchmark ist ein gängiger Standard zur Bewertung der Leistungsfähigkeit von OLTP-Systemen (Online Transaction Processing). Das Skript simuliert eine Reihe von Transaktionen wie Bestellungen, Zahlungen, Bestellstatusabfragen, Lieferungen und Lagerbestandsprüfungen, um die Leistung des SQL Servers zu messen.

Voraussetzungen
Tcl-Interpreter (Version 8.6 oder höher)
SQL Server mit TPC-C Schema-Datenbank
ODBC-Treiber für SQL Server (z.B. "ODBC Driver 18 for SQL Server")
Konfigurationsoptionen
Die folgenden Konfigurationsparameter sind im Skript editierbar:

library: Das zu ladende SQL Server-Bibliothekspaket (tdbc::odbc).
version: Version der SQL Server-Bibliothek.
total_iterations: Anzahl der Transaktionen, die vor dem Beenden des Skripts ausgeführt werden.
RAISEERROR: Gibt an, ob das Skript bei einem SQL Server-Fehler beendet werden soll (true oder false).
KEYANDTHINK: Simuliert Benutzer-Eingabezeit und Denkzeit (true oder false).
CHECKPOINT: Führt nach Abschluss des Tests einen SQL Server-Checkpoint durch (true oder false).
rampup: Dauer der Einlaufphase in Minuten, bevor die Transaktionszählung beginnt.
duration: Dauer des Testzeitraums in Minuten.
mode: Betriebsmodus des Skripts (Local oder Primary).
authentication: Authentifizierungsmethode für den SQL Server (windows, sql oder entra).
server: Name oder IP-Adresse des SQL Servers.
port: Portnummer des SQL Servers (Standard: 1433).
odbc_driver: Name des ODBC-Treibers.
uid: Benutzername für SQL Server Authentifizierung.
pwd: Passwort für SQL Server Authentifizierung.
tcp: Verwendung des TCP-Protokolls (true oder false).
azure: Verbindung zu einer Azure SQL-Datenbank (true oder false).
database: Name der Datenbank mit dem TPC-C Schema.
encrypt: Verschlüsselung der Verbindung (true oder false).
trust_cert: Vertrauen in das Serverzertifikat (true oder false).
msi_object_id: MSI-Objekt-ID für Entra-Authentifizierung (optional).
Ausführung
Stellen Sie sicher, dass alle oben genannten Voraussetzungen erfüllt sind.
Passen Sie die Konfigurationsoptionen im Skript an Ihre Umgebung an.
Starten Sie das Skript mit einem Tcl-Interpreter.
Funktionsweise
Datenbankverbindung: Das Skript stellt eine Verbindung zum SQL Server her und wählt die TPC-C-Datenbank aus.
Ramp-up: Das System wird durch eine Einlaufphase vorbereitet, in der Transaktionen ausgeführt werden, ohne dass die Leistung gemessen wird.
Transaktionsausführung: Es werden verschiedene TPC-C-Transaktionen (Bestellung, Zahlung, etc.) durchgeführt.
Leistungsmessung: Nach der Einlaufphase misst das Skript die Leistung des SQL Servers, indem es die Anzahl der Transaktionen pro Minute erfasst.
Abschluss: Nach Abschluss des Tests werden die Ergebnisse ausgegeben und alle Ressourcen freigegeben.
Fehlerbehandlung
Das Skript enthält grundlegende Fehlerbehandlung, um auf Probleme während der Ausführung zu reagieren.
Wenn RAISEERROR auf true gesetzt ist, wird das Skript bei einem SQL Server-Fehler abgebrochen.
