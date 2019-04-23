---
title: Installieren von SQL Server-Beispieldatenbanken | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: afc99ba7d5b7a6b5cf9fc0e610160213dec5d2e8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654502"
---
# <a name="install-sql-server-sample-databases"></a>Installieren von SQL Server-Beispieldatenbanken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beispieldatenbanken sind nützlich für das Experimentieren mit SQL und LINQ-Abfragen, Datenbindung, Entity Framework-Modellierung und So weiter.  Jedes Produkt-Datenbank verfügt über eine eigene Beispieldatenbanken. Sind zwei gängige SQL Server-Beispieldatenbanken Northwind und AdventureWorks.  
  
 **AdventureWorks** ist die aktuelle Beispieldatenbank für SQL Server-Produkte bereitgestellt. Sie können es herunterladen, wie eine MDF-Datei aus dem [Seite "AdventureWorks" auf Codeplex](http://msftdbprodsamples.codeplex.com/). Hier sind regelmäßige und einfache (LT) Versionen der Datenbank verfügbar. In den meisten Fällen wird die Version LT bevorzugt, da sie weniger komplex ist.  
  
 **Northwind** ist eine relativ einfache SQL Server-Datenbank, die seit vielen Jahren verwendet wurde. Sie können es herunterladen, als bak-Datei aus der [Seite der Northwind-Datenbank auf CodePlex](https://northwinddatabase.codeplex.com/). Entzippen Sie die Datei in den neuen Ordner, der nicht unter Ihrem Ordner "Benutzer" ist, um Berechtigungsprobleme zu vermeiden.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Zum Wiederherstellen einer Datenbank aus einer bak-Datei in Visual Studio  
  
1.  Wenn Sie eine Microsoft SQL Server-Datenbank sichern, ist das Ergebnis einer bak-Datei an. Um die bak als Datenbankdatei wieder verwendbaren Datei machen zu können, muss er *wiederhergestellt*. Wählen Sie im Hauptmenü **Ansicht** > **Objekt-Explorer von SQL Server**. Wenn Sie nicht angezeigt wird, müssen Sie es zu installieren. Wechseln Sie zu **Systemsteuerung** > **Programme und Funktionen**, suchen Sie Microsoft Visual Studio 2015, und klicken Sie auf die **Änderung** Schaltfläche. Wenn die Liste der installierten Komponenten im Installationsfenster angezeigt wird, wählen Sie die **Objekt-Explorer von SQL Server** Kontrollkästchen, und klicken Sie dann mit der Installation fortfahren.  
  
2.  In SQL Server Objekt-Explorer mit der Maustaste alle SQL Server-Datenbank-Engine (z. B. Localdb), und wählen**neue Abfrage**.  
  
     ![Neue Abfrage für SQL Server-Objekt-Explorer](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "Raddata neue Abfrage für SQL Server-Objekt-Explorer")  
  
3.  Zunächst benötigen Sie die logischen Namen, der die Datenbank und Protokolldateien in der BAK-Datei. Um es zu erhalten, geben Sie auf diese Abfrage in den SQL-Abfrage-Editor, und wählen Sie dann auf die grüne **ausführen** Schaltfläche am oberen Rand des Fensters. Ändern Sie den Dateipfad, sofern erforderlich, um auf die BAK-Datei zu verweisen.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Notieren Sie sich die logischen Namen an, die im Ergebnisfenster angezeigt werden.  Für die Northwind-Datenbank sind die beiden logischen Namen Northwind und Northwind_log.  
  
4.  Führen Sie nun diese Abfrage zum Erstellen der Datenbank. Ersetzen Sie Ihre eigenen Quell-und Zielpfad, logische Datenbanknamen und den physischen Dateinamen für Northwind nach Bedarf. Behalten Sie die MDF- und LDF Dateierweiterungen.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  SQL Server Objekt-Explorer mit der Maustaste auf die **Datenbanken** Knoten, und Sie sollten finden Sie unter den Knoten der Northwind-Datenbank. Falls nicht, klicken Sie dann mit der rechten Maustaste auf Datenbanken, und wählen **neue Datenbank hinzufügen**. Geben Sie den Namen und den Speicherort der MDF-Datei, die Sie gerade erstellt haben.  
  
6.  Die Datenbank ist jetzt bereit, die als eine Datenquelle in Visual Studio verwendet.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Zum Wiederherstellen einer Datenbank aus einer bak-Datei in SQL Server Management Studio  
  
1.  Laden Sie SQL Server Management Studio herunter, von der Downloadwebsite aus.  
  
2.  In SSMS **Objekt-Explorer** Fenster mit der rechten Maustaste die **Datenbanken** Knoten**Restore Database**, und geben Sie den Speicherort der BAK-Datei.  
  
     ![SSMS Restore Database](../data-tools/media/raddata-ssms-restore-database.png "Raddata SSMS Restore Database")
