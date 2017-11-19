---
title: Aktualisieren Sie die MDF-Dateien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 8ed511eed7b0ace46bbc61c1d486ade608d4b5a5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="upgrade-mdf-files"></a>Aktualisieren Sie die MDF-Dateien
Dieses Thema beschreibt die Optionen für die Datenbankdatei (.mdf) aktualisieren, nach der Installation einer neueren Version von Visual Studio. Enthält Sie Anweisungen für die folgenden Aufgaben:  
  
-   Aktualisieren einer Datenbankdatei, um eine neuere Version von SQL Server Express LocalDB zu verwenden.  
  
-   Aktualisieren Sie eine Datenbankdatei, um eine neuere Version von SQL Server Express verwenden  
  
-   Mit einer Datenbankdatei in Visual Studio arbeiten Sie, aber behalten Sie der Kompatibilität mit einer älteren Version von SQL Server Express oder LocalDB bei  
  
-   Stellen Sie die SQL Server Express das Standard-Datenbankmodul  
  
Sie können Visual Studio verwenden, um ein Projekt zu öffnen, die eine Datenbankdatei (.mdf) enthält, die mit einer älteren Version von SQL Server Express oder LocalDB erstellt wurde. Allerdings um den Vorgang fortzusetzen, um das Projekt in Visual Studio entwickeln, benötigen Sie diese Version von SQL Server Express oder LocalDB auf dem gleichen Computer wie Visual Studio installiert, oder Sie müssen ein upgrade der Datenbankdatei. Wenn Sie die Datenbankdatei aktualisieren, können Sie keine Zugriffsberechtigung mit älteren Versionen von SQL Server Express oder LocalDB.  
  
Sie können außerdem aufgefordert, eine Datenbankdatei zu aktualisieren, die über eine frühere Version von SQL Server Express oder LocalDB erstellt wurde, wenn die Version der Datei ist nicht kompatibel mit der Instanz von SQL Server Express oder LocalDB, die derzeit installiert ist. Um das Problem zu beheben, fordert Visual Studio Sie auf die Datei zu aktualisieren.  
  
> [!IMPORTANT]
> Es wird empfohlen, dass Sie die Datenbankdatei sichern, bevor Sie das Upgrade ausgeführt.  
  
> [!WARNING]
> Wenn Sie eine MDF-Datei, die in LocalDB 2014 (V12) 32-Bit auf LocalDB 2016 (V13) oder höher erstellt wurde aktualisieren, werden Sie nicht mehr öffnen die Datei in der 32-Bit-Version von LocalDB sein.
  
Vor dem upgrade einer Datenbank sollten Sie der folgenden Kriterien:  
  
-   Aktualisieren Sie nicht, wenn Sie auf das Projekt in einer älteren Version und eine neuere Version von Visual Studio arbeiten möchten.  
  
-   Aktualisieren Sie nicht, wenn Ihre Anwendung in Umgebungen verwendet werden, die SQL Server Express statt LocalDB zu verwenden.  
  
-   Wenn Ihre Anwendung Remoteverbindungen verwendet nicht aktualisiert werden, weil LocalDB anerkennen nicht.  
  
-   Aktualisieren Sie nicht, wenn Ihre Anwendung auf Internet Information Services (IIS) verwendet.  
  
-   Erwägen Sie ein Upgrade aus, wenn Sie datenbankanwendungen in einer Sandbox-Umgebung testen möchten, aber nicht zum Verwalten eine Datenbank verwendet werden soll.  
  
### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>So aktualisieren Sie eine Datenbankdatei um die LocalDB-Version zu verwenden.
  
1.  In **Server-Explorer**, wählen die **mit Datenbank verbinden** Schaltfläche.  
  
2.  In der **Verbindung hinzufügen** Dialogfeld geben die folgende Informationen:  
  
    -   **Datenquelle**:`Microsoft SQL Server (SqlClient)`  
  
    -   **Servernamen**:  
  
        -   Die Standardversion verwendet: `(localdb)\MSSQLLocalDB`.  Dadurch wird die ProjectV12 oder ProjectV13, angegeben, je nachdem welche Version von Visual Studio installiert ist und wann die erste LocalDB-Instanz erstellt wurde. Die **MSSQLLocalDB** Knoten **Objekt-Explorer von SQL Server** zeigt, welche Version ist es auf verweist.  
  
        -   Um eine bestimmte Version verwenden: `(localdb)\ProjectsV12` oder `(localdb)\ProjectsV13`, wobei V12 LocalDB 2014 und V13 LocalDB 2016 ist.  
  
    -   **Anfügen einer Datenbankdatei**: den physischen Pfad der primären MDF-Datei.  
  
    -   **Logischer Name**: der Name, den Sie mit der Datei verwenden möchten.  
  
3.  Klicken Sie auf die Schaltfläche **OK**.  
  
4.  Wenn Sie aufgefordert werden, wählen Sie die **Ja** Schaltfläche, um die Datei zu aktualisieren.  
  
    Die Datenbank aktualisiert wird, wird mit dem Datenbankmodul LocalDB angefügt und ist nicht mehr kompatibel mit der älteren Version von LocalDB.  
  
Sie können auch eine SQL Server Express-Verbindung, um LocalDB zu verwenden, indem Sie das Kontextmenü für die Verbindung öffnen und anschließend ändern **Verbindung ändern**. In der **Verbindung ändern** Dialogfeld Feld, ändern Sie den Namen des `(LocalDB)\MSSQLLocalDB`. In der **erweiterte Eigenschaften** Dialogfeld Feld, stellen Sie sicher, dass **Benutzerinstanz** festgelegt ist, um **"false"**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>So aktualisieren Sie eine Datenbankdatei, um die Version von SQL Server Express verwenden  
  
1.  Wählen Sie im Kontextmenü für die Verbindung mit der Datenbank, **Verbindung ändern**.  
  
2.  In der **Verbindung ändern** wählen Sie im Dialogfeld die **erweitert** Schaltfläche.  
  
3.  In der **erweiterte Eigenschaften** wählen Sie im Dialogfeld die **OK** Schaltfläche ohne Ändern des Servernamens.  
  
    Die Datenbankdatei wird aktualisiert, dass die aktuelle Version von SQL Server Express übereinstimmt.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Mit der Datenbank in Visual Studio arbeiten, aber beibehalten der Kompatibilität mit SQL Server Express  
  
-   Öffnen Sie das Projekt in Visual Studio ohne dass eine Aktualisierung.  
  
    -   Wählen Sie zum Ausführen des Projekts die **F5** Schlüssel.  
  
    -   Um die Datenbank zu bearbeiten, öffnen Sie die MDF-Datei in **Projektmappen-Explorer**, und erweitern Sie den Knoten im **Server-Explorer** Arbeit mit Ihrer Datenbank.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Um SQL Server Express, das Standard-Datenbankmodul zu machen.  
  
1.  Wählen Sie auf der Menüleiste **Tools**, **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie die **Datenbanktools** Optionen, und wählen Sie dann **Datenverbindungen**.  
  
3.  In der **SQL Server-Instanzname** Text geben den Namen der Instanz von SQL Server Express oder LocalDB, die Sie verwenden möchten. Wenn die Instanz die Bezeichnung befindet sich nicht, geben Sie `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.  
  
4.  Klicken Sie auf die Schaltfläche **OK**.  
  
    SQL Server Express wird das Standard-Datenbankmodul für Ihre Anwendungen.

## <a name="see-also"></a>Siehe auch
[Zugreifen auf Daten in Visual Studio](accessing-data-in-visual-studio.md)
