---
title: Übersicht über lokale Daten | Microsoft-Dokumentation
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
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 94b3f066a66a380875609b4f6485d56a19ebde3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885576"
---
# <a name="local-data-overview"></a>Übersicht über lokale Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Data-Anwendungen zu entwickeln, ist es, damit Sie in der Produktion immer noch keine Fehler einbauen, in der Regel empfohlen, eine lokale Kopie einer Datenbank zu verwenden. Potenzielle Probleme auch gemeinsame Nutzung einer Testdatenbank mit anderen Entwicklern erstellt werden, wenn zwei Entwickler Fehler einführen, die schwer zu erkennenden Arten miteinander interagieren können. Sie können alle diese Fehlerquellen vermeiden, indem Sie eigene Testdaten auf Ihrem lokalen Computer. Die meisten, wenn nicht alle Systeme Datenbank können Sie lokale Datendateien zu erstellen. Für .NET-Projekte bietet Visual Studio spezielle Unterstützung für lokale SQL Server-Datenbankdateien (.mdf) und Microsoft Access-Datenbankdateien (.mdb).  
  
 Visual Studio unterstützt folgende Szenarien:  
  
1.  
  
2.  
  
- 
  
- 
  
- Ein SQL Server-Datenbankprojekt erstellen, klicken Sie auf den Projektmappenknoten im Projektmappen-Explorer und auswählen **hinzufügen &#124; neues Projekt**.  Wählen Sie im linken Bereich **SQL Server &#124; Datenbank** Projekt, und klicken Sie auf OK. Klicken Sie im Projektmappen-Explorer klicken Sie mit der rechten Maustaste auf den Datenbank-Projektknoten, um eine lokale Datenbankdatei zu importieren, und dann Entwickeln der Anwendung die Verbindung mit der Datenbank, die vom Projekt erstellt. Gut, wenn Sie entwickeln und ändern das Datenbankschema zur gleichen Zeit, dass Sie die Anwendung entwickeln.  
  
   ![Datenbank in Datenbankprojekt importieren](../data-tools/media/raddata-import-database-into-database-project.png "Raddata Importdatenbank in Datenbankprojekt")  
  
- Wenn Sie eine neue Datenbank erstellen, fügen Sie zuerst eine **dienstbasierte Datenbankdatei** zu Ihrem Projekt (**Projekt &#124; neues Element hinzufügen)**. Dadurch wird eine neue MDF-Datei, die mit der SQL Server-Standardinstanz auf dem lokalen Computer, wird standardmäßig verbunden ist (Localdb) \MSSQLocalDB wird erstellt. Die Datenbank sollte im Server-Explorer angezeigt werden. Erweitern Sie den Knoten, und mit der rechten Maustaste auf den Knoten zum Hinzufügen neuer Datenbankobjekte wie Tabellen, Sichten, Funktionen und So weiter.  
  
  Weitere Informationen zu SQL Server Express LocalDB, finden Sie unter [Einführung von LocalDB, ein verbessertes SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) und [LocalDB: steht für meine Datenbank?](http://go.microsoft.com/fwlink/?LinkId=234376) auf der Microsoft-Website.  
  
  Die folgende Tabelle enthält Links zu Themen, in denen beschrieben wird, wie die Anwendung mit lokalen Daten verbunden wird:  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen einer SQL­-Datenbank mithilfe eines Designers](../data-tools/create-a-sql-database-by-using-a-designer.md)|Enthält schrittweise Anweisungen zum Erstellen einer lokalen Datenbankdatei, die zum Testen von Datenfunktionen sowie zum Erstellen von Anwendungen verwendet werden kann.|  
|[Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Enthält schrittweise Anweisungen zum Herstellen einer Verbindung mit einer SQL Server Express LocalDB-Datenbank, während Sie eine einfache Windows-Anwendung erstellen.|  
|[Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Enthält Schritt-für-Schritt-Anweisungen zum Herstellen einer Verbindung mit einer Microsoft Access-Datenbank.|  
|[Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Enthält Anweisungen zum Herstellen einer Verbindung mit der Beispieldatenbank Northwind in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express und Access.|  
  
## <a name="use-the-connection-string"></a>Verwenden Sie die Verbindungszeichenfolge  
 Dies ist der einfachste Ansatz und ist eine gute Wahl, wenn Ihre Anwendung nur aus der Datenbank liest und Drittanbieter-Datenbanken verwenden. Die Datenbankdatei kann sich an einem beliebigen auf dem lokalen Computer sein, die Ihre Anwendung verfügt über die Berechtigung zum Zugreifen auf und, die das Datenbanksystem unterstützt.  
  
1.  (Optional) Erstellen Sie eine neue Verbindung, wie im [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md). Für Drittanbieter-Datenbanken und MDF-Dateien für die Sie bereits wissen, die Verbindungszeichenfolge und nicht Datenbindung durchführen oder mithilfe einer Datenquelle, z. B. Entity Framework-Klassen oder Datasets, ist dieser Schritt nicht erforderlich. Verwenden Sie einfach die Verbindungszeichenfolge zur Verbindung mit der lokalen Datei. MDF-Dateien finden Sie unter [MDF-Dateien aktualisieren](../data-tools/upgrade-dot-mdf-files.md) und [Herstellen der Verbindung](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Optional) Bei Verwendung von Entity Framework oder LINQ to SQL, Datasets erstellen Sie die Datenquelle, mit dem Assistenten zur Datenquellenkonfiguration. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Hinzufügen einer vorhandenen-.mdf zu Ihrem Projekt  
 Wenn Ihre Anwendung einfügen, löschen oder Aktualisieren von Daten und eine Kopie der ursprünglichen Datei verfügbar bleiben sollen, sollten Sie dem Projekt die Datei hinzugefügt. Wenn Sie dies tun, können Sie die Item-Eigenschaft festlegen, darauf, um **in Ausgabeverzeichnis kopieren** zu **immer kopieren** oder **kopieren, wenn neuer**, und die Anwendung zu entwickeln. Jedes Mal, wenn Sie die Anwendung, erstellen die ursprüngliche Datenbank wird in den Ausgabeordner kopiert und die Kopie Ihrer Anwendung Änderungen ausgeführt werden. Auf diese Weise haben Sie immer eine bereinigten Kopie der ursprünglichen Daten.  
  
1.  Verwendung **Windows Datei-Explorer** ziehen und Ablegen der MDF-Datei vom aktuellen Speicherort auf den Projektknoten im Projektmappen-Explorer in Visual Studio.  Wenn die Datei bereits mit einer LocalDB-Instanz angefügt ist, müssen Sie ihn zuerst trennen. Nachdem Sie ihn in das Projekt ablegen, wird Visual Studio automatisch mit der Standardinstanz von LocalDB erneut an.  
  
2.  Mit der rechten Maustaste auf den neuen Knoten für die Datenbank, und wählen Sie Eigenschaften. Wählen Sie entweder das Kopierverhalten **immer kopieren** oder **kopieren, wenn neuer**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Erstellen eines SQL Server-Datenbankprojekts und importieren Sie Ihre Datenbank  
 Dies ist eine gute Option, wenn Sie die Datenbank selbst entwickeln werden werden, z. B. Spalten oder Tabellen hinzufügen oder Ändern von Datentypen.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Jedes Projekt enthält zwei Kopien der Datenbank  
 Wenn Sie ein Projekt erstellen, kann die Datenbankdatei im Stammordner des Projekts kopiert werden, in der Ausgabe **Bin**, Ordner. Dieses Verhalten hängt die **in Ausgabeverzeichnis kopieren** -Eigenschaft der Datei, und der Standardwert dieser Eigenschaft hängt von den Typ der Datenbankdatei, die Sie verwenden.  
  
 Anzeigen der **Bin** Ordner **Projektmappen-Explorer**, wählen Sie die **alle Dateien anzeigen** auf der Symbolleiste auf die Schaltfläche.  
  
> [!NOTE]
>  Die **in Ausgabeverzeichnis kopieren** Eigenschaft trifft nicht auf Web- oder C++-Projekte.  
  
 Die Datenbankdatei im Stammordner des Projekts wird nur geändert, wenn Sie das Datenbankschema oder die Daten bearbeiten **Server-Explorer**/**Datenbank-Explorer** oder andere [Visual Datenbanktools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Wenn Sie Daten während der Anwendungsentwicklung ändern, ändern Sie die Datenbank in der **Bin** Ordner. Wenn Sie beispielsweise die Taste F5 drücken, um die Anwendung zu debuggen, werden Sie mit der Datenbank in diesem Ordner verbunden.  
  
|Wert von **in Ausgabeverzeichnis kopieren** Eigenschaft|Verhalten|  
|----------------------------------------------------|--------------|  
|**Kopieren, wenn neuer** (Standardwert für SDF-Dateien)|Die Datenbankdatei wird kopiert, aus dem Projektverzeichnis in das **Bin** Verzeichnis beim ersten, die Sie das Projekt erstellen. Die **Änderungsdatum** Eigenschaft der Dateien wird dann verglichen, jedes Mal, die Sie das Projekt erneut erstellen. Wenn die Datei im Projektordner neuer ist, wird Sie kopiert die **Bin** Ordner ersetzt die vorherige Datei. Andernfalls werden keine Dateien kopiert. **Vorsicht:** nicht empfohlen, diesen Wert für MDB- oder MDF-Dateien. Die Datenbankdatei kann sogar geändert werden, wenn sich die Daten nicht ändern. Die Datei kann als neuer, wenn Sie sich einfach um eine Verbindung öffnen gekennzeichnet werden (z. B. durch Erweitern der **Tabellen** Knoten **Server-Explorer**).|  
|**Immer kopieren** (Standardwert für MDF- und MDB-Dateien)|Die Datenbankdatei wird kopiert, aus dem Projektverzeichnis in das **Bin** Verzeichnis jedes Mal, die Sie Ihre Anwendung erstellen. Alle an der Datendatei im Ausgabeordner vorgenommenen Änderungen werden beim nächsten Ausführen der Anwendung überschrieben.|  
|**Nicht kopieren**|Das System überschreibt niemals die Datei in die **Bin** Verzeichnis. Die Anwendung erstellt eine dynamische Verbindungszeichenfolge, die auf die Datenbankdatei im Ausgabeverzeichnis verweist. Daher müssen Sie die Datei manuell in das Ausgabeverzeichnis kopieren, wenn die Daten im Ausgabeverzeichnis den Daten im Projektverzeichnis entsprechen sollen.|  
  
## <a name="common-issues-with-local-data"></a>Häufig auftretende Probleme bei lokalen Daten  
 In der folgenden Tabelle werden Probleme erläutert, die beim Verwenden von lokalen Datendateien auftreten können.  
  
|Problem|Erklärung|  
|-----------|-----------------|  
|Jedes Mal, wenn ich die Anwendung teste und Daten ändere, gehen die Änderungen beim nächsten Ausführen der Anwendung verloren.|Der Wert des der **in Ausgabeverzeichnis kopieren** Eigenschaft **kopieren, wenn neuer** oder **immer kopieren**. Die Datenbank im Ausgabeordner (die Datenbank, die beim Testen der Anwendung geändert wird) bei jeder Erstellung des Projekts überschrieben. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten von lokalen Datendateien in Ihr Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Es wird eine Meldung mit dem Hinweis angezeigt, dass die Datendatei gesperrt ist.|Access (MDB-Dateien): Stellen Sie sicher, dass die Datei nicht in einem anderen Programm, z. B. Access, geöffnet ist.<br /><br /> SQL Server Express (MDF-Dateien): SQL Express sperrt die Datendatei, wenn Sie versuchen, sie außerhalb der Visual Studio IDE zu kopieren, zu verschieben oder umzubenennen.|  
|Der Zugriff wird verweigert, wenn mehrere Benutzer gleichzeitig versuchen, auf dieselbe Datenbank zuzugreifen.|Visual Studio nutzt *Benutzerinstanzen*, dies ist ein Feature von SQL Server Express, die eine separate Instanz von SQL Server für jeden Benutzer erstellt. Sobald ein Benutzer auf die Datei zugreift, kann kein nachfolgender Benutzer eine Verbindung herstellen. Dieses Problem kann z. B. auftreten, wenn Sie versuchen, eine Webanwendung gleichzeitig in ASP.NET Development Server und in Internet Information Services (IIS) auszuführen, da IIS i. d. R. unter einem anderen Konto ausgeführt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verbinden mit Daten in einer lokalen Datenbankdatei (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)