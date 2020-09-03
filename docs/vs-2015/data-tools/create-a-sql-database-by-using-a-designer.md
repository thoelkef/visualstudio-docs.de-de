---
title: Erstellen einer SQL-Datenbank mit einem Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651062"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Erstellen einer SQL-­Datenbank mithilfe eines Designers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Visual Studio können Sie eine lokale Datenbankdatei in SQL Server Express localdb erstellen und aktualisieren, um grundlegende Aufgaben wie das Hinzufügen von Tabellen und das Definieren von Spalten zu untersuchen. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie erweiterte Funktionen ermitteln, indem Sie die lokale Datenbank als Ausgangspunkt für andere exemplarische Vorgehensweisen verwenden, in denen sie erforderlich ist.

 Sie können eine Datenbank auch erstellen, indem Sie SQL Server Management Studio (ein separates herunterladen) oder Transact-SQL-Anweisungen im **SQL Server-Objekt-Explorer** Tool Fenster in Visual Studio verwenden.

 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:

- [Erstellen eines Projekts und einer lokalen Datenbankdatei](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Erstellen von Tabellen, Spalten, primär Schlüsseln und Fremdschlüsseln](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Auffüllen der Tabellen mit Daten](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Voraussetzungen
 Um diese exemplarische Vorgehensweise abzuschließen, stellen Sie sicher, dass Sie SQL Server Data Tools installiert haben. Im Menü **Ansicht** sollte **SQL Server-Objekt-Explorer**angezeigt werden. Wenn dies nicht der Fall ist, wechseln **Sie zu Software**, klicken Sie auf **Visual Studio 2015**, wählen Sie **ändern**aus, und aktivieren Sie das Kontrollkästchen neben **SQL Server Data Tools**.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> Erstellen eines Projekts und einer lokalen Datenbankdatei

#### <a name="to-create-a-project-and-a-database-file"></a>So erstellen Sie ein Projekt und eine Datenbankdatei

1. Erstellen Sie ein Windows Forms Projekt mit dem Namen `SampleDatabaseWalkthrough` .

2. Wählen Sie in der Menüleiste die Option **Projekt**  >  **Neues Element hinzufügen**aus.

3. Scrollen Sie in der Liste der Element Vorlagen nach unten, und wählen Sie **Dienst basierte Datenbank**aus.

    ![Dialogfeld "Elementvorlagen"](../data-tools/media/raddata-vsitemtemplates.png "raddata-vsitemtemplates")

4. Nennen Sie die Datenbank **SampleDatabase**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

5. Wenn das **Datenquellen** Fenster nicht geöffnet ist, öffnen Sie es, indem Sie die Tasten UMSCHALT + ALT + D auswählen, oder wählen Sie **View**in der Menüleiste  >  **andere Windows**-  >  **Datenquellen**anzeigen aus.

6. Wählen Sie im Fenster **Datenquellen** den Link **neue Datenquelle hinzufügen** aus.

7. Wählen Sie im **Assistenten zum Konfigurieren von Datenquellen**viermal die Schaltfläche **weiter** aus, um die Standardeinstellungen zu übernehmen, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

   Wenn Sie das Eigenschaftenfenster für die Datenbank öffnen, können Sie ihre Verbindungszeichenfolge und den Speicherort der primären MDF-Datei anzeigen. Sie werden feststellen, dass sich die Datenbankdatei im Projektordner befindet.

- Wählen Sie in Visual Studio **Ansicht**  >  **SQL Server-Objekt-Explorer** aus, wenn dieses Fenster nicht bereits geöffnet ist. Öffnen Sie das Eigenschaften Fenster, indem Sie den Knoten **Datenverbindungen** erweitern, das Kontextmenü für SampleDatabase. mdf öffnen und dann **Eigenschaften**auswählen.

- Sie können auch **View**  >  **Server-Explorer**auswählen, wenn dieses Fenster nicht bereits geöffnet ist. Öffnen Sie das Eigenschaften Fenster, indem Sie den Knoten **Datenverbindungen** erweitern. Öffnen Sie das Kontextmenü für SampleDatabase. mdf, und wählen Sie dann **Eigenschaften**aus.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> Erstellen von Tabellen, Spalten, primär Schlüsseln und Fremdschlüsseln
 In diesem Abschnitt erstellen Sie einige Tabellen, einen Primärschlüssel in jeder Tabelle und einige wenige Zeilen mit Beispieldaten. In der folgenden exemplarischen Vorgehensweise erhalten Sie eine Vorstellung davon, wie diese Informationen möglicherweise in einer Anwendung angezeigt werden. Sie erstellen auch einen Fremdschlüssel, um ggf. anzugeben, wie Datensätze in einer Tabelle den Datensätzen in einer anderen Tabelle entsprechen.

#### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers

1. Erweitern Sie in **Server-Explorer** oder **SQL Server-Objekt-Explorer**den Knoten **Datenverbindungen** , und erweitern Sie dann den Knoten **SampleDatabase. mdf** .

2. Öffnen Sie das Kontextmenü für **Tabellen**, und wählen Sie dann **neue Tabelle hinzufügen**aus.

     Der **Tabellen-Designer** wird geöffnet und zeigt ein Raster mit einer Standardzeile an, die eine einzelne Spalte in der Tabelle darstellt, die Sie erstellen. Durch Hinzufügen von Zeilen zum Raster fügen Sie zusätzliche Spalten in der Tabelle hinzu.

3. Im Raster fügen Sie eine Zeile für jeden der folgenden Einträge hinzu:

    |Spaltenname|Datentyp|NULL zulassen|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (gelöscht)|
    |`CompanyName`|`nvarchar(50)`|False (gelöscht)|
    |`ContactName`|`nvarchar (50)`|True (ausgewählt)|
    |`Phone`|`nvarchar (24)`|True (ausgewählt)|

4. Öffnen Sie das Kontextmenü für die `CustomerID` Zeile, und wählen Sie dann **Primärschlüssel festlegen**aus.

5. Öffnen Sie das Kontextmenü für die Standardzeile, und wählen Sie dann **Löschen**aus.

6. Benennen Sie die Tabelle "Customers", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Die Ausgabe sollte in etwa wie folgt aussehen:

     ![Tabellen-Designer](../data-tools/media/raddata-table-designer.png "raddata-Tabellen-Designer")

7. Klicken Sie in der oberen linken Ecke der **Tabellen-Designer**auf die Schaltfläche **Aktualisieren** .

8. Klicken Sie im Dialogfeld **Vorschau der Daten Bank Updates** auf die Schaltfläche **Datenbank aktualisieren** .

     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

#### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders

1. Fügen Sie eine weitere Tabelle hinzu, und fügen Sie dann in der folgenden Tabelle eine Zeile für jeden Eintrag hinzu:

    |Spaltenname|Datentyp|NULL zulassen|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (gelöscht)|
    |`CustomerID`|`nchar(5)`|False (gelöscht)|
    |`OrderDate`|`datetime`|True (ausgewählt)|
    |`OrderQuantity`|`int`|True (ausgewählt)|

2. Legen Sie **OrderID** als Primärschlüssel fest, und löschen Sie dann die Standardzeile.

3. Benennen Sie die Tabelle "Orders", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. Klicken Sie in der oberen linken Ecke der **Tabellen-Designer**auf die Schaltfläche **Aktualisieren** .

5. Klicken Sie im Dialogfeld **Vorschau der Daten Bank Updates** auf die Schaltfläche **Datenbank aktualisieren** .

     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

#### <a name="to-create-a-foreign-key"></a>So erstellen Sie einen Fremdschlüssel

1. Öffnen Sie im Kontext Bereich auf der rechten Seite des Rasters das Kontextmenü für **Fremdschlüssel**, und wählen Sie dann **neuen Fremdschlüssel hinzufügen**aus, wie in der folgenden Abbildung dargestellt.

     ![Hinzufügen eines Fremdschlüssels im Tabellen-Designer](../data-tools/media/foreignkey.png "ForeignKey")

2. Ersetzen Sie im angezeigten Textfeld **ToTable** durch `Customers` .

3. Aktualisieren Sie im Bereich T-SQL die letzte Zeile, sodass Sie mit dem folgenden Beispiel übereinstimmt:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. Klicken Sie in der oberen linken Ecke der **Tabellen-Designer**auf die Schaltfläche **Aktualisieren** .

5. Klicken Sie im Dialogfeld **Vorschau der Daten Bank Updates** auf die Schaltfläche **Datenbank aktualisieren** .

     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> Auffüllen der Tabellen mit Daten

#### <a name="to-populate-the-tables-with-data"></a>So füllen Sie die Tabellen mit Daten

1. Erweitern Sie in **Server-Explorer** oder **SQL Server-Objekt-Explorer**den Knoten für die Beispieldatenbank.

2. Öffnen Sie das Kontextmenü für den Knoten **Tabellen** , wählen Sie **Aktualisieren**aus, und erweitern Sie dann den Knoten **Tabellen** .

3. Öffnen Sie das Kontextmenü für die Tabelle Customers, und wählen Sie dann **Tabellendaten anzeigen**aus.

4. Fügen Sie die gewünschten Daten für mindestens drei Kunden hinzu.

     Sie können fünf beliebige Zeichen für die Kunden-IDs angeben, wählen Sie aber mindestens eine aus, an die Sie sich noch erinnern können, um sie später in dieser Prozedur zu verwenden.

5. Öffnen Sie das Kontextmenü für die Tabelle Orders, und wählen Sie dann **Tabellendaten anzeigen**aus.

6. Fügen Sie Daten für mindestens drei Bestellungen hinzu.

    > [!IMPORTANT]
    > Überprüfen Sie, ob alle Bestellnummern und -mengen ganze Zahlen sind und ob jede Kunden-ID mit einem Wert übereinstimmt, den Sie in der Spalte "CustomerID" in der Tabelle "Customers" angegeben haben.

7. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern**.

8. Wählen Sie in der Menüleiste **Datei**  >  **Schließen**Projekt Mappe aus.

    > [!NOTE]
    > Die empfohlene Vorgehensweise besteht darin, die soeben erstellte Datenbankdatei zu sichern, indem Sie sie kopieren und dann entweder die Kopie an einem anderen Speicherort einzufügen oder der Kopie einen anderen Namen zu geben.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun über eine lokale Datenbankdatei mit einigen Beispiel Daten verfügen, können Sie eine der exemplarischen Vorgehensweisen für Datenbankaufgaben ausführen.
