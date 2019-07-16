---
title: Erstellen Sie eine Datenbankdatei und Tabellen-Designer
description: In diesem Tutorial, die beschreibt, wie Sie Tabellen und Fremdschlüssel in einer Datenbank hinzufügen, mit der Tabellen-Designer in Visual Studio. Es wird gezeigt, wie Daten über die grafische Oberfläche hinzufügen.
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6f227a7948f5a842120341432c03747119988ddf
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501072"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Eine Datenbank erstellen und Hinzufügen von Tabellen in Visual Studio

Sie können Visual Studio zum Erstellen und Aktualisieren einer lokalen Datenbankdatei in SQL Server Express LocalDB verwenden. Sie können auch eine Datenbank erstellen, durch Ausführen von Transact-SQL-Anweisungen in der **Objekt-Explorer von SQL Server** Toolfenster in Visual Studio. In diesem Thema erstellen wir eine *mdf* -Datei und fügen Sie Tabellen und Schlüsseln mit der Tabellen-Designer.

## <a name="prerequisites"></a>Vorraussetzungen

Um diese exemplarische Vorgehensweise abzuschließen, benötigen Sie die optionale **datenspeicherung und-Verarbeitung** arbeitsauslastung in Visual Studio installiert. Öffnen Sie sie zur Installation **Visual Studio-Installer** , und wählen Sie **ändern** oder **weitere** > **ändern** neben der Version von Visual Studio, die Sie ändern möchten.

::: moniker range=">=vs-2019"

Auf der **Workloads** Registerkarte **andere Toolsets**, wählen Sie **datenspeicherung und-Verarbeitung**, und klicken Sie dann auf **ändern** die Workload hinzufügen Visual Studio.

::: moniker-end

::: moniker range="=vs-2017"

Auf der **Workloads** Registerkarte **Web und Cloud**, wählen Sie **datenspeicherung und-Verarbeitung**, und klicken Sie dann auf **ändern** die Workload hinzufügen Visual Studio.

::: moniker-end

## <a name="create-a-project-and-a-local-database-file"></a>Erstellen eines Projekts und einer lokalen Datenbankdatei

1. Erstellen Sie ein neues **Windows Forms-App** Projekt, und nennen Sie sie **SampleDatabaseWalkthrough**.

2. Wählen Sie auf der Menüleiste **Projekt** > **neues Element hinzufügen**.

3. In der Liste der Vorlagen einen Bildlauf nach unten, und wählen Sie **Dienstbasierte Datenbank**.

     ![Dialogfeld "Elementvorlagen"](../data-tools/media/raddata-vsitemtemplates.png)

4. Nennen Sie die Datenbank **"SampleDatabase"** , und klicken Sie dann auf **hinzufügen**.

### <a name="add-a-data-source"></a>Hinzufügen einer Datenquelle

1. Wenn die **Datenquellen** Fenster nicht geöffnet ist, öffnen Sie sie durch Drücken von **UMSCHALT**+**Alt**+**D** oder auswählen **Ansicht** > **Other Windows** > **Datenquellen** in der Menüleiste.

1. In der **Datenquellen** wählen Sie im Fenster der **neue Datenquelle hinzufügen** Link.

   Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

1. Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank** und wählen Sie dann **Weiter**.

1. Auf der **Auswählen eines Datenbankmodells** Seite **Weiter** auf den Standardwert (Dataset) zu übernehmen.

1. Auf der **wählen Sie Ihre Datenverbindung** Seite die **SampleDatabase.mdf** -Datei in der Dropdown Liste, und wählen Sie dann **Weiter**.

1. Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite **Weiter**.

1. Eine der **Datenbankobjekte auswählen** Seite sehen, da Sie eine Nachricht die Datenbank keine Objekte enthalten. Klicken Sie auf **Fertig stellen**.

### <a name="view-properties-of-the-data-connection"></a>Anzeigen der Eigenschaften von der Datenverbindung

Sehen Sie die Verbindungszeichenfolge für die *SampleDatabase.mdf* Datei durch Öffnen des Eigenschaftenfensters der Datenverbindung:

- Wählen Sie **Ansicht** > **Objekt-Explorer von SQL Server** zum Öffnen der **Objekt-Explorer von SQL Server** Fenster. Erweitern Sie **(Localdb) \MSSQLLocalDB** > **Datenbanken**, und klicken Sie dann mit der rechten Maustaste auf *SampleDatabase.mdf* , und wählen Sie **Eigenschaften**.

- Alternativ können Sie auswählen **Ansicht** > **Server-Explorer**, sofern diese nicht bereits geöffnet ist. Öffnen Sie das Eigenschaftenfenster durch Erweitern der **Datenverbindungen** Knoten, öffnen das Kontextmenü für *SampleDatabase.mdf*, und wählen Sie dann **Eigenschaften**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Erstellen von Tabellen und Schlüsseln mit Tabellen-Designer

In diesem Abschnitt erstellen Sie zwei Tabellen, einen Primärschlüssel in jeder Tabelle und einige Zeilen der Beispieldaten. Sie erstellen auch einen foreign Key, um anzugeben, wie Datensätze in einer Tabelle mit Datensätzen in einer anderen Tabelle entsprechen.

### <a name="create-the-customers-table"></a>Erstellen der Customers-Tabelle

1. In **Server-Explorer**, erweitern Sie die **Datenverbindungen** Knoten, und erweitern Sie dann die **SampleDatabase.mdf** Knoten.

2. Öffnen Sie das Kontextmenü für **Tabellen**, und wählen Sie dann **neue Tabelle hinzufügen**.

     Der **Tabellen-Designer** wird geöffnet und zeigt ein Raster mit einer Standardzeile an, die eine einzelne Spalte in der Tabelle darstellt, die Sie erstellen. Durch Hinzufügen von Zeilen zum Raster fügen Sie zusätzliche Spalten in der Tabelle hinzu.

3. Im Raster fügen Sie eine Zeile für jeden der folgenden Einträge hinzu:

    |Spaltenname|Datentyp|NULL zulassen|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (gelöscht)|
    |`CompanyName`|`nvarchar(50)`|False (gelöscht)|
    |`ContactName`|`nvarchar (50)`|True (ausgewählt)|
    |`Phone`|`nvarchar (24)`|True (ausgewählt)|

4. Öffnen Sie das Kontextmenü für die `CustomerID` Zeile, und wählen Sie dann **Primärschlüssel festlegen**.

5. Öffnen Sie das Kontextmenü für die Standardzeile, und wählen Sie dann **löschen**.

6. Benennen Sie die Tabelle "Customers", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Folgendes sollte angezeigt werden:

    ![Tabellen-Designer](../data-tools/media/raddata-table-designer.png)

7. In der oberen linken Ecke des **Tabellen-Designer**Option **Update**.

8. In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld **Update Database**.

    Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

### <a name="create-the-orders-table"></a>Erstellen Sie die Orders-Tabelle

1. Fügen Sie eine weitere Tabelle hinzu, und fügen Sie dann in der folgenden Tabelle eine Zeile für jeden Eintrag hinzu:

    |Spaltenname|Datentyp|NULL zulassen|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (gelöscht)|
    |`CustomerID`|`nchar(5)`|False (gelöscht)|
    |`OrderDate`|`datetime`|True (ausgewählt)|
    |`OrderQuantity`|`int`|True (ausgewählt)|

2. Legen Sie **"OrderID"** als Primärschlüssel aus, und löschen Sie dann die Standardzeile.

3. Benennen Sie die Tabelle "Orders", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4. In der oberen linken Ecke des der **Tabellen-Designer**, wählen die **Update** Schaltfläche.

5. In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld die **Update Database** Schaltfläche.

    Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

### <a name="create-a-foreign-key"></a>Erstellen eines Fremdschlüssels

1. Klicken Sie im Kontextbereich auf der rechten Seite des Rasters öffnen Sie das Kontextmenü für **Fremdschlüssel**, und wählen Sie dann **neuen Fremdschlüssel hinzufügen**, wie in die folgende Abbildung dargestellt.

     ![Hinzufügen eines Fremdschlüssels im Tabellen-Designer](../data-tools/media/foreignkey.png)

2. Ersetzen Sie im angezeigten Textfeld **ToTable** durch **Customers**.

3. Aktualisieren Sie die letzte Zeile entsprechend der im folgende Beispiel in T-SQL-Bereich:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. In der oberen linken Ecke des der **Tabellen-Designer**, wählen die **Update** Schaltfläche.

5. In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld die **Update Database** Schaltfläche.

    Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

## <a name="populate-the-tables-with-data"></a>Füllen Sie die Tabellen mit Daten

1. In **Server-Explorer** oder **Objekt-Explorer von SQL Server**, erweitern Sie den Knoten für die Beispieldatenbank.

2. Öffnen Sie das Kontextmenü für die **Tabellen** Knoten **aktualisieren**, und erweitern Sie dann die **Tabellen** Knoten.

3. Öffnen Sie das Kontextmenü für die Customers-Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.

4. Fügen Sie beliebige Daten, die Sie für einige Kunden möchten hinzu.

    Sie können fünf beliebige Zeichen für die Kunden-IDs angeben, wählen Sie aber mindestens eine aus, an die Sie sich noch erinnern können, um sie später in dieser Prozedur zu verwenden.

5. Öffnen Sie das Kontextmenü für die Orders-Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.

6. Hinzufügen von Daten für einige Aufträge.

    > [!IMPORTANT]
    > Überprüfen Sie, ob alle Bestellnummern und -mengen ganze Zahlen sind und ob jede Kunden-ID mit einem Wert übereinstimmt, den Sie in der Spalte **CustomerID** in der Tabelle „Customers“ angegeben haben.

7. Wählen Sie auf der Menüleiste **Datei** > **Alles speichern**.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](accessing-data-in-visual-studio.md)
