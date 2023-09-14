# fuppes
Spielerliste von Fortuna Düsseldorf laut Wiki Tabelle für Lernzwecke fit gemacht




-- Erstelle die Tabelle für Spieler
CREATE TABLE Spieler (
    spieler_id INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(255),
    Beginn INT, -- Jahr des Spielbeginns
    Ende INT -- Jahr des Spielendes
);

-- Erstelle die Tabelle für Spielerwerte
CREATE TABLE SiegeUndTore (
    siegeundtore_id INT AUTO_INCREMENT PRIMARY KEY,
    spieler_id INT,
    Ligasieg INT,
    Ligator INT,
    Pokalsieg INT,
    Pokaltor INT,
    Europasieg INT,
    Europator INT,
    Sonstigesieg INT,
    Sonstigetor INT,
    Gesamtsiege INT,
    Gesamttore INT,
    FOREIGN KEY (spieler_id) REFERENCES Spieler(spieler_id)
);




LOAD DATA INFILE '/pfad/zur/deiner/csv/datei.csv'
INTO TABLE Spieler
FIELDS TERMINATED BY ',' -- Trennzeichen in deiner CSV-Datei
LINES TERMINATED BY '\n' -- Zeilentrennzeichen in deiner CSV-Datei
IGNORE 1 ROWS -- Wenn die erste Zeile in der CSV-Datei Spaltenüberschriften enthält, ansonsten entferne diese Zeile
(Name, Beginn, Ende); -- Ordne die CSV-Spalten den Tabellenspalten in Spieler zu

LOAD DATA INFILE '/pfad/zur/deiner/csv/datei.csv'
INTO TABLE SiegeUndTore
FIELDS TERMINATED BY ',' -- Trennzeichen in deiner CSV-Datei
LINES TERMINATED BY '\n' -- Zeilentrennzeichen in deiner CSV-Datei
IGNORE 1 ROWS -- Wenn die erste Zeile in der CSV-Datei Spaltenüberschriften enthält, ansonsten entferne diese Zeile
(Name, Ligasieg, Ligator, Pokalsieg, Pokaltor, Europasieg, Europator, Sonstigesieg, Sonstigetor, Gesamtsiege, Gesamttore); -- Ordne die CSV-Spalten den Tabellenspalten in SiegeUndTore zu
