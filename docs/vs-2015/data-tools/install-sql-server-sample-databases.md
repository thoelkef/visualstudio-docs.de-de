---
title: Installieren von SQL Server-Beispiel Datenbanken | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3991d3b741162b4b1993e5359ad427c17f00321a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651525"
---
# <a name="install-sql-server-sample-databases"></a>Installieren von SQL Server-Beispieldatenbanken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beispiel Datenbanken sind nützlich, um mit SQL-und LINQ-Abfragen, DataBinding, Entity Framework Modellierung usw. zu experimentieren.  Jedes Datenbankprodukt verfügt über eigene Beispiel Datenbanken. Northwind und AdventureWorks sind zwei beliebte SQL Server-Beispiel Datenbanken.

 **AdventureWorks** ist die aktuelle Beispieldatenbank, die für SQL Server-Produkte bereitgestellt wird. Sie können Sie als MDF-Datei von der Seite " [AdventureWorks" auf CodePlex](http://msftdbprodsamples.codeplex.com/)herunterladen. Hier sind reguläre und Lightweight (lt)-Versionen der Datenbank verfügbar. In den meisten Szenarien wird die lt-Version bevorzugt, da Sie weniger komplex ist.

 **Northwind** ist eine relativ einfache SQL Server Datenbank, die seit vielen Jahren verwendet wurde. Sie können Sie als BAK-Datei von der [Northwind-Datenbankseite auf CodePlex](https://northwinddatabase.codeplex.com/)herunterladen. Um Berechtigungsprobleme zu vermeiden, entzippen Sie die Datei in einen neuen Ordner, der nicht in Ihrem Benutzerordner gespeichert ist.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>So stellen Sie eine Datenbank aus einer BAK-Datei in Visual Studio wieder her

1. Wenn Sie eine Microsoft SQL Server Datenbank sichern, ist das Ergebnis eine BAK-Datei. Damit die BAK-Datei wieder als Datenbankdatei verwendbar ist, muss Sie wieder *hergestellt*werden. Wählen Sie im Hauptmenü  >  SQL Server-Objekt-Explorer **anzeigen** aus. Wenn Sie es nicht sehen, müssen Sie es möglicherweise installieren. Wechseln Sie zur **Systemsteuerung**  > **Programme und Funktionen**, suchen Sie Microsoft Visual Studio 2015, und klicken Sie auf die Schaltfläche **ändern** . Wenn die Liste der installierten Komponenten im Installationsfenster angezeigt wird, aktivieren Sie das Kontrollkästchen **SQL Server-Objekt-Explorer** , und fahren Sie dann mit der Installation fort.

2. Klicken Sie in SQL Server-Objekt-Explorer mit der rechten Maustaste auf eine beliebige SQL Server Datenbank-Engine (z. b. localdb), und wählen Sie**neue Abfrage**aus.

     ![Neue Abfrage SQL Server-Objekt-Explorer](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server-Objekt-Explorer neue Abfrage")

3. Zunächst benötigen Sie die logischen Namen der Datenbank und der Protokolldateien in der BAK-Datei. Um es zu erhalten, geben Sie diese Abfrage in den SQL-Abfrage-Editor ein, und klicken Sie dann oben im Fenster auf die grüne Schaltfläche **Ausführen** . Ändern Sie ggf. den Dateipfad, um auf die BAK-Datei zu verweisen.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Notieren Sie sich die logischen Namen, die im Fenster Ergebnisse angezeigt werden.  Für die Northwind-Datenbank sind die beiden logischen Namen Northwind und Northwind_log.

4. Führen Sie diese Abfrage jetzt aus, um die Datenbank zu erstellen. Ersetzen Sie nach Bedarf Ihre eigenen Quell-und Zielpfade, logische Datenbanknamen und physische Dateinamen für Northwind. Behalten Sie die MDF-und LDF-Dateierweiterungen bei.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. Klicken Sie in SQL Server-Objekt-Explorer mit der rechten Maustaste auf den Knoten **Datenbanken** , und der Northwind-Datenbankknoten sollte angezeigt werden. Wenn nicht, klicken Sie mit der rechten Maustaste auf Datenbanken, und wählen Sie **neue Datenbank hinzufügen**aus. Geben Sie den Namen und den Speicherort der MDF-Datei ein, die Sie soeben erstellt haben.

6. Die Datenbank kann nun als Datenquelle in Visual Studio verwendet werden.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>So stellen Sie eine Datenbank aus einer BAK-Datei in SQL Server Management Studio wieder her

1. Laden Sie SQL Server Management Studio von der Download Website herunter.

2. Klicken Sie im **Objekt-Explorer** Fenster von SSMS mit der rechten Maustaste auf den Knoten **Datenbanken** , wählen Sie**Datenbank wiederherstellen**aus, und geben Sie den Speicherort der BAK-Datei an.

     ![SSMS-Wiederherstellungs Datenbank](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS RESTORE DATABASE")
