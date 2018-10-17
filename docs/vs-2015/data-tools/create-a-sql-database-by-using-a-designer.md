---
title: Erstellen Sie eine SQL­Datenbank mithilfe eines Designers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8a1765c142fcf039b28b2e1c2e6ad1bf7038aaa9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220752"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Erstellen Sie eine SQL­Datenbank mithilfe eines Designers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können untersuchen, grundlegende Aufgaben wie dem Hinzufügen von Tabellen und Definieren von Spalten mithilfe von Visual Studio zum Erstellen und Aktualisieren einer lokalen Datenbankdatei in SQL Server Express LocalDB. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie erweiterte Funktionen ermitteln, indem Sie die lokale Datenbank als Ausgangspunkt für andere exemplarische Vorgehensweisen verwenden, in denen sie erforderlich ist.  
  
 Sie können auch eine Datenbank erstellen, mithilfe von SQL Server Management Studio (separater Download) oder Transact-SQL-Anweisungen in der **Objekt-Explorer von SQL Server** Toolfenster in Visual Studio.  
  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:  
  
-   [Erstellen eines Projekts und einer lokalen Datenbankdatei](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [Erstellen von Tabellen, Spalten, Primärschlüssel und Fremdschlüssel](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [Füllen Sie die Tabellen mit Daten](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise abgeschlossen haben, stellen Sie sicher, dass Sie SQL Server Data Tools installiert haben. Auf der **Ansicht** Menü sollte **Objekt-Explorer von SQL Server**. Wenn sie nicht vorhanden ist, fahren Sie mit **Programme hinzufügen oder entfernen**, klicken Sie auf **Visual Studio 2015**wählen **ändern**, und aktivieren Sie das Kontrollkästchen neben **SQL Server Data Tools**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> Erstellen eines Projekts und einer lokalen Datenbankdatei  
  
#### <a name="to-create-a-project-and-a-database-file"></a>So erstellen Sie ein Projekt und eine Datenbankdatei  
  
1.  Erstellen Sie ein Windows Forms-Projekt mit dem Namen `SampleDatabaseWalkthrough`.  
  
2.  Wählen Sie auf der Menüleiste **Projekt** > **neues Element hinzufügen**.  
  
3.  In der Liste der Vorlagen einen Bildlauf nach unten, und wählen Sie **Dienstbasierte Datenbank**.  
  
     ![Im Dialogfeld "Vorlagen" Element](../data-tools/media/raddata-vsitemtemplates.png "Raddata VSItemTemplates")  
  
4.  Nennen Sie die Datenbank **"SampleDatabase"**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
5.  Wenn die **Datenquellen** Fenster nicht geöffnet ist, öffnen sie hierzu die Tasten UMSCHALT + Alt + D oder wählen Sie in der Menüleiste auswählen **Ansicht** > **Other Windows**  >  **Datenquellen**.  
  
6.  In der **Datenquellen** wählen Sie im Fenster der **neue Datenquelle hinzufügen** Link.  
  
7.  In der **Assistenten zur Datenquellenkonfiguration**, wählen die **Weiter** Schaltfläche viermal auf die Standardeinstellungen übernehmen, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
 Wenn Sie das Eigenschaftenfenster für die Datenbank öffnen, können Sie ihre Verbindungszeichenfolge und den Speicherort der primären MDF-Datei anzeigen. Sie werden feststellen, dass die Datenbankdatei im Projektordner.  
  
-   Wählen Sie in Visual Studio **Ansicht** > **Objekt-Explorer von SQL Server** , wenn diese nicht bereits geöffnet ist. Öffnen Sie das Eigenschaftenfenster durch Erweitern der **Datenverbindungen** Knoten, öffnen das Kontextmenü für "SampleDatabase.mdf", und wählen dann **Eigenschaften**.  
  
-   Alternativ können Sie auswählen **Ansicht** > **Server-Explorer**, sofern diese nicht bereits geöffnet ist. Öffnen Sie das Eigenschaftenfenster durch Erweitern der **Datenverbindungen** Knoten. Öffnen Sie das Kontextmenü für "SampleDatabase.mdf", und wählen Sie dann **Eigenschaften**.  
  
##  <a name="BKMK_CreateNewTbls"></a> Erstellen von Tabellen, Spalten, Primärschlüssel und Fremdschlüssel  
 In diesem Abschnitt erstellen Sie einige Tabellen, einen Primärschlüssel in jeder Tabelle und einige wenige Zeilen mit Beispieldaten. In der folgenden exemplarischen Vorgehensweise erhalten Sie eine Vorstellung davon, wie diese Informationen möglicherweise in einer Anwendung angezeigt werden. Sie erstellen auch einen Fremdschlüssel, um ggf. anzugeben, wie Datensätze in einer Tabelle den Datensätzen in einer anderen Tabelle entsprechen.  
  
#### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers  
  
1.  In **Server-Explorer** oder **Objekt-Explorer von SQL Server**, erweitern Sie die **Datenverbindungen** Knoten, und erweitern Sie dann die **SampleDatabase.mdf**Knoten.  
  
2.  Öffnen Sie das Kontextmenü für **Tabellen**, und wählen Sie dann **neue Tabelle hinzufügen**.  
  
     Die **Tabellen-Designer** wird geöffnet und zeigt ein Raster mit einer standardmäßigen Zeile an, die eine einzelne Spalte in der Tabelle darstellt, die Sie erstellen. Durch Hinzufügen von Zeilen zum Raster fügen Sie zusätzliche Spalten in der Tabelle hinzu.  
  
3.  Im Raster fügen Sie eine Zeile für jeden der folgenden Einträge hinzu:  
  
    |Spaltenname|Datentyp|NULL zulassen|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (gelöscht)|  
    |`CompanyName`|`nvarchar(50)`|False (gelöscht)|  
    |`ContactName`|`nvarchar (50)`|True (ausgewählt)|  
    |`Phone`|`nvarchar (24)`|True (ausgewählt)|  
  
4.  Öffnen Sie das Kontextmenü für die `CustomerID` Zeile, und wählen Sie dann **Primärschlüssel festlegen**.  
  
5.  Öffnen Sie das Kontextmenü für die Standardzeile, und wählen Sie dann **löschen**.  
  
6.  Benennen Sie die Tabelle "Customers", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     Folgendes sollte angezeigt werden:  
  
     ![Tabellen-Designer](../data-tools/media/raddata-table-designer.png "Raddata Tabellen-Designer")  
  
7.  In der oberen linken Ecke des der **Tabellen-Designer**, wählen die **Update** Schaltfläche.  
  
8.  In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld die **Update Database** Schaltfläche.  
  
     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.  
  
#### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders  
  
1.  Fügen Sie eine weitere Tabelle hinzu, und fügen Sie dann in der folgenden Tabelle eine Zeile für jeden Eintrag hinzu:  
  
    |Spaltenname|Datentyp|NULL zulassen|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (gelöscht)|  
    |`CustomerID`|`nchar(5)`|False (gelöscht)|  
    |`OrderDate`|`datetime`|True (ausgewählt)|  
    |`OrderQuantity`|`int`|True (ausgewählt)|  
  
2.  Legen Sie **"OrderID"** als Primärschlüssel aus, und löschen Sie dann die Standardzeile.  
  
3.  Benennen Sie die Tabelle "Orders", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  In der oberen linken Ecke des der **Tabellen-Designer**, wählen die **Update** Schaltfläche.  
  
5.  In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld die **Update Database** Schaltfläche.  
  
     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.  
  
#### <a name="to-create-a-foreign-key"></a>So erstellen Sie einen Fremdschlüssel  
  
1.  Klicken Sie im Kontextbereich auf der rechten Seite des Rasters öffnen Sie das Kontextmenü für **Fremdschlüssel**, und wählen Sie dann **neuen Fremdschlüssel hinzufügen**, wie in die folgende Abbildung dargestellt.  
  
     ![Hinzufügen eines Fremdschlüssels im Tabellen-Designer](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  Ersetzen Sie in das Textfeld, das angezeigt wird, **ToTable** mit `Customers`.  
  
3.  Aktualisieren Sie die letzte Zeile entsprechend der im folgende Beispiel in T-SQL-Bereich:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  In der oberen linken Ecke des der **Tabellen-Designer**, wählen die **Update** Schaltfläche.  
  
5.  In der **Vorschau der Datenbankupdates** wählen Sie im Dialogfeld die **Update Database** Schaltfläche.  
  
     Ihre Änderungen werden in der lokalen Datenbankdatei gespeichert.  
  
##  <a name="BKMK_Populating"></a> Füllen Sie die Tabellen mit Daten  
  
#### <a name="to-populate-the-tables-with-data"></a>So füllen Sie die Tabellen mit Daten  
  
1.  In **Server-Explorer** oder **Objekt-Explorer von SQL Server**, erweitern Sie den Knoten für die Beispieldatenbank.  
  
2.  Öffnen Sie das Kontextmenü für die **Tabellen** Knoten **aktualisieren**, und erweitern Sie dann die **Tabellen** Knoten.  
  
3.  Öffnen Sie das Kontextmenü für die Customers-Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.  
  
4.  Fügen Sie die gewünschten Daten für mindestens drei Kunden hinzu.  
  
     Sie können fünf beliebige Zeichen für die Kunden-IDs angeben, wählen Sie aber mindestens eine aus, an die Sie sich noch erinnern können, um sie später in dieser Prozedur zu verwenden.  
  
5.  Öffnen Sie das Kontextmenü für die Orders-Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.  
  
6.  Fügen Sie Daten für mindestens drei Bestellungen hinzu.  
  
    > [!IMPORTANT]
    >  Überprüfen Sie, ob alle Bestellnummern und -mengen ganze Zahlen sind und ob jede Kunden-ID mit einem Wert übereinstimmt, den Sie in der Spalte "CustomerID" in der Tabelle "Customers" angegeben haben.  
  
7.  Wählen Sie auf der Menüleiste **Datei** > **Alles speichern**.  
  
8.  Wählen Sie auf der Menüleiste **Datei** > **Projektmappe schließen**.  
  
    > [!NOTE]
    >  Die empfohlene Vorgehensweise besteht darin, die soeben erstellte Datenbankdatei zu sichern, indem Sie sie kopieren und dann entweder die Kopie an einem anderen Speicherort einzufügen oder der Kopie einen anderen Namen zu geben.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nun, da Sie eine lokale Datenbankdatei mit einigen Beispieldaten haben, können Sie eine der exemplarischen Vorgehensweisen abschließen, die Tasks der Datenbank zu veranschaulichen.

