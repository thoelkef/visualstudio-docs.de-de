---
title: "&#220;bersicht &#252;ber lokale Daten | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Zugriff, .mdb-Dateien in Visual Studio"
  - "Daten [Visual Studio], Lokal"
  - "Datenzugriff [Visual Studio], Problembehandlung"
  - "Lokale Daten"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, Lokale Daten"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# &#220;bersicht &#252;ber lokale Daten
Wenn Sie lokale Daten verwenden, verbinden Sie die Anwendung mit einer Datenbankdatei auf dem lokalen Computer statt mit einer Datenbank auf einem separaten Server.  Beispielsweise können Sie eine Anwendung, die Sie in Visual Studio entwickeln, mit den folgenden lokalen Datenbankdateien verbinden:  
  
-   SQL Server Express LocalDB\-Datenbankdateien \(.mdf\)  
  
-   SQL Server Express\-Datenbankdateien \(.mdf\)  
  
-   Microsoft Access\-Datenbankdateien \(.mdb\)  
  
 Die folgende Tabelle enthält Links zu Themen, in denen beschrieben wird, wie die Anwendung mit lokalen Daten verbunden wird:  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[Exemplarische Vorgehensweise: Erstellen einer lokalen Datenbankdatei in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)|Enthält schrittweise Anweisungen zum Erstellen einer lokalen Datenbankdatei, die zum Testen von Datenfeatures sowie zum Erstellen von Anwendungen verwendet werden kann.|  
|[Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Enthält schrittweise Anweisungen zum Herstellen einer Verbindung mit einer SQL Server Express LocalDB\-Datenbank, während Sie eine einfache Windows\-Anwendung erstellen.|  
|[Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Access\-Datenbank \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Enthält Schritt\-für\-Schritt\-Anweisungen zum Herstellen einer Verbindung mit einer Microsoft Access\-Datenbank.|  
|[Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Enthält Anweisungen zum Herstellen einer Verbindung mit der Beispieldatenbank Northwind in [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)], SQL Server Compact, SQL Server Express und Access.|  
  
 Nachdem Sie eine Datenquelle erstellt und für den Zugriff auf eine lokale Datendatei konfiguriert haben, verwenden Sie zur Arbeit mit den Daten dieselben Technologien und Objekte, die Sie auch zum Arbeiten mit Daten aus allen anderen Quellen verwenden würden.  Weitere Informationen finden Sie unter [Erstellen von Datenanwendungen](../data-tools/creating-data-applications.md).  
  
## Integration der Datenbank in die Anwendung  
 Wenn Sie eine Verbindung mit lokalen Daten herstellen, können Sie nicht nur eine Verbindung mit einer Datenbankdatei herstellen, sondern sie auch in die Anwendung integrieren.  So können Sie z. B. das Menü **Projekt** öffnen, zu einer vorhandenen SDF\-, MDF\- bzw. MDB\-Datei navigieren und sie anschließend dem Projekt hinzufügen.  
  
 Wenn Sie lokale Datendateien hinzufügen, erstellen Sie ein typisiertes Dataset sowie eine dynamische Verbindungszeichenfolge, die auf die Datenbankdatei in der Anwendung verweist.  Wenn Sie dem Projekt eine Datenbankdatei hinzufügen, verwenden Sie den **Assistenten zum Konfigurieren von Datenquellen** zum Festlegen der Objekte, die im Dataset enthalten sein sollen.  
  
> [!NOTE]
>  Sie können die Verbindung automatisch konfigurieren und den **Assistenten zum Konfigurieren von Datenquellen** starten, indem Sie eine SDF\-, MDF\- oder MDB\-Datei aus dem Datei\-Explorer in den **Projektmappen\-Explorer** ziehen.  Anschließend können Sie die Objekte auswählen, die in der Anwendung verwendet werden sollen.  
  
 Wenn Sie den **Assistenten zum Konfigurieren von Datenquellen** zum Erstellen der Datenquelle für eine lokale Datendatei verwenden, werden Sie aufgefordert, die Datei in das Projekt einzubinden.  Andernfalls enthält die Anwendung lediglich die Verbindungszeichenfolge, die auf den hartcodierten Pfad verweist, jedoch nicht die eigentliche Datendatei.  Weitere Informationen finden Sie unter [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
 Nachdem Sie den Assistenten beendet haben, werden die Datenbankdatei und das Dataset im **Projektmappen\-Explorer**\/**Datenbank\-Explorer** angezeigt, und die angegebenen Datenbankobjekte werden im Fenster **Datenquellen** angezeigt.  Sie können Steuerelemente erstellen, die an die zugrunde liegenden Daten gebunden sind, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.  Öffnen Sie das Menü **Daten**, und wählen Sie die Option **Datenquellen anzeigen** aus, um das Fenster **Datenquellen** zu öffnen.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Verwenden einer Datenbankdatei  
 Bevor Sie eine vorhandene Datenbankdatei \(.mdf\) in Visual Studio verwenden können, müssen Sie die Datei möglicherweise in eine [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)]\-Datenbankdatei konvertieren.  Wenn Sie eine Verbindung mit einer vorhandenen Datenbankdatei herstellen, wird eine Meldung mit der Frage angezeigt, ob Sie eine Aktualisierung durchführen möchten.  
  
> [!IMPORTANT]
>  Wenn Sie die Datenbankdatei \(.mdf\) aktualisieren, können Sie sie nicht in einer früheren Version von SQL Server öffnen.  
  
 Sie müssen die Datenbankdatei \(.mdf\) nicht umzuwandeln, wenn der **SQL Server\-Instanzname** auf SQLEXPRESS festgelegt und SQL Server 2008 Express installiert ist.  SQL Server 2008 Express wird installiert, wenn Visual Studio 2010 installiert wird.  Um den Instanznamen für diese Datenbankdatei zu ändern, öffnen Sie Visual Studio, öffnen Sie das Dialogfeld **Verbindung hinzufügen**, legen Sie `.\SQLEXPRESS` als Servernamen fest, und geben Sie anschließend die Datenbank bzw. den Datenbankdateinamen an.  
  
## SQL Server Express LocalDB und SQL Server Express  
 Sie können eine dienstbasierte Datenbankdatei \(.mdf\) einem beliebigen Projekt in Visual Studio hinzufügen.  Sie können Designer in Visual Studio verwenden, um Tabellen und andere Datenbankobjekte zu entwerfen, und Sie können Abfragen ausführen.  
  
 Wenn Sie eine dienstbasierte Datenbank in Visual Studio erstellen, wird das SQL Server Express LocalDB\-Modul verwendet, um auf die Datenbankdatei \(.mdf\) zuzugreifen, wobei in früheren Versionen von Visual Studio das SQL Server Express\-Modul verwendet wurde.  
  
 SQL Server Express LocalDB ist eine einfache Version von SQL Server, deren Programmierung sich größtenteils ähnlich gestaltet wie die einer SQL Server\-Datenbank.  SQL Server Express LocalDB wird im Benutzermodus ausgeführt, und Sie können es mit weniger erforderlichen Komponenten und ohne Konfiguration schneller installieren.  
  
> [!NOTE]
>  Weitere Informationen zu SQL Server Express LocalDB finden Sie unter [Einführung von LocalDB, ein verbessertes SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) und [LocalDB: Wo ist Meine Datenbank?](http://go.microsoft.com/fwlink/?LinkId=234376) auf der Microsoft\-Website.  
  
 In Visual Studio können Sie standardmäßig SQL Server Express statt SQL Server Express LocalDB verwenden.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  Wählen Sie unter dem Knoten **Datenbanktools** die Option **Datenverbindungen** aus.  Geben Sie im Textfeld **SQL Server\-Instanzname** `SQLEXPRESS` ein.  Alternativ können Sie weitere Werte für den SQL Server\-Instanz\-Namen eingeben \(beispielsweise `SQL2008`\).  
  
 In der folgenden Tabelle werden Unterschiede zwischen den Modulen SQL Server Express LocalDB und SQL Server Express beschrieben.  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|Datenbanktyp beim Erstellen einer dienstbasierten Datenbank|In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] und [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], SQL Server Express LocalDB|In Visual Studio 2010 und älter, SQL Server Express|  
|Name der SQL Server\-Instanz in Extras\/Optionen|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|Wert der Datenquelle in der Verbindungszeichenfolge|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|Wert von AttachDbFilename in der Verbindungszeichenfolge|Dateipfad|Dateipfad|  
|Benutzerinstanz ist erforderlich \("User Instance\=True" in Verbindungszeichenfolge\)|Nein|Ja|  
|Erweiterung der Datenbankdatei|.mdf|.mdf|  
  
## Vorteile von SQL Server Express LocalDB  
  
-   SQL Server Express LocalDB ist mit dienstbasierten Editionen von SQL Server für die Funktionen kompatibel, die SQL Server Express LocalDB aktiviert.  In SQL Server können Sie jede beliebige Datenbank oder jeden beliebigen Transact\-SQL\-Code von SQL Server Express LocalDB zu SQL Server oder SQL Azure ohne Upgradeschritte verschieben.  Daher können Sie SQL Server Express LocalDB verwenden, um Anwendungen für alle Versionen von SQL Server zu entwickeln.  
  
-   SQL Server Express LocalDB unterstützt den gleichen Abfrageoptimierer und Abfrageprozessor, den höheren Versionen von SQL Server verwenden.  
  
## Jedes Projekt enthält zwei Kopien der Datenbank  
 Wenn Sie ein Projekt erstellen, wird die Datenbankdatei möglicherweise aus dem Stammordner des Projekts in den Ausgabeordner **bin** kopiert.  Dieses Verhalten hängt von der Eigenschaft **In Ausgabeverzeichnis kopieren** der Datei ab, und der Standardwert dieser Eigenschaft hängt vom Typ der verwendeten Datenbankdatei ab.  
  
 Klicken Sie auf der Symbolleiste auf die Schaltfläche **Alle Dateien anzeigen**, um den Ordner **bin** im **Projektmappen\-Explorer** anzuzeigen.  
  
> [!NOTE]
>  Die Eigenschaft **In Ausgabeverzeichnis kopieren** gilt nicht für Web\- oder C\+\+\-Projekte.  
  
 Die Datenbankdatei im Stammordner des Projekts wird nur geändert, wenn Sie mit dem **Server\-Explorer**\/**Datenbank\-Explorer** oder anderen [Visual Database Tools](http://msdn.microsoft.com/de-de/6b145922-2f00-47db-befc-bf351b4809a1) das Datenbankschema oder die Daten bearbeiten.  
  
 Wenn Sie Daten während der Anwendungsentwicklung ändern, ändern Sie die Datenbank im Ordner **bin**.  Wenn Sie beispielsweise die Taste F5 drücken, um die Anwendung zu debuggen, werden Sie mit der Datenbank in diesem Ordner verbunden.  
  
|Wert der Eigenschaft **In Ausgabeverzeichnis kopieren**|Verhalten|  
|-------------------------------------------------------------|---------------|  
|**Kopieren, wenn neuer** \(Standardwert für SDF\-Dateien\)|Die Datenbankdatei wird beim ersten Erstellen des Projekts aus dem Projektverzeichnis in das Verzeichnis **bin** kopiert.  Jedes Mal, wenn Sie das Projekt erneut erstellen, wird dann ein Vergleich mit der Eigenschaft **Geändert am** der Dateien durchgeführt.  Wenn die Datei im Projektordner neuer ist, wird sie in den Ordner **bin** kopiert und ersetzt die vorherige Datei.  Andernfalls werden keine Dateien kopiert. **Caution:**  Dieser Wert wird nicht für MDB\- oder MDF\-Dateien empfohlen.  Die Datenbankdatei kann sogar geändert werden, wenn sich die Daten nicht ändern.  Die Datei kann als neuer gekennzeichnet werden, wenn Sie einfach einen Verbindungsknoten \(z. B. durch Erweitern des Knotens **Tabellen**\) im **Server\-Explorer** öffnen.|  
|**Immer kopieren** \(Standardwert für MDF\- und MDB\-Dateien\)|Bei jedem Erstellen der Anwendung wird die Datenbankdatei aus dem Projektverzeichnis in das Verzeichnis **bin** kopiert.  Alle an der Datendatei im Ausgabeordner vorgenommenen Änderungen werden beim nächsten Ausführen der Anwendung überschrieben.|  
|**Nicht kopieren**|Das System überschreibt niemals die Datei im Verzeichnis **bin**.  Die Anwendung erstellt eine dynamische Verbindungszeichenfolge, die auf die Datenbankdatei im Ausgabeverzeichnis verweist.  Daher müssen Sie die Datei manuell in das Ausgabeverzeichnis kopieren, wenn die Daten im Ausgabeverzeichnis den Daten im Projektverzeichnis entsprechen sollen.|  
  
## Häufig auftretende Probleme bei lokalen Daten  
 In der folgenden Tabelle werden Probleme erläutert, die beim Verwenden von lokalen Datendateien auftreten können.  
  
|Problem|Erklärung|  
|-------------|---------------|  
|Jedes Mal, wenn ich die Anwendung teste und Daten ändere, gehen die Änderungen beim nächsten Ausführen der Anwendung verloren.|Der Wert der Eigenschaft **In Ausgabeverzeichnis kopieren** ist **Kopieren, wenn neuer** oder **Immer kopieren**.  Die Datenbank im Ausgabeordner \(die Datenbank, die beim Testen der Anwendung geändert wird\) bei jeder Erstellung des Projekts überschrieben.  Weitere Informationen finden Sie unter [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Es wird eine Meldung mit dem Hinweis angezeigt, dass die Datendatei gesperrt ist.|Access \(MDB\-Dateien\): Stellen Sie sicher, dass die Datei nicht in einem anderen Programm, z. B. Access, geöffnet ist.<br /><br /> SQL Server Express \(MDF\-Dateien\): SQL Express sperrt die Datendatei, wenn Sie versuchen, sie außerhalb der Visual Studio IDE zu kopieren, zu verschieben oder umzubenennen.|  
|Der Zugriff wird verweigert, wenn mehrere Benutzer gleichzeitig versuchen, auf dieselbe Datenbank zuzugreifen.|Visual Studio verwendet *Benutzerinstanzen*, eine Funktion von SQL Server Express, die eine separate Instanz von SQL Server für jeden Benutzer erstellt.  Sobald ein Benutzer auf die Datei zugreift, kann kein nachfolgender Benutzer eine Verbindung herstellen.  Dieses Problem kann z. B. auftreten, wenn Sie versuchen, eine Webanwendung gleichzeitig in ASP.NET Development Server und in Internet Information Services \(IIS\) auszuführen, da IIS i. d. R. unter einem anderen Konto ausgeführt wird.|  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Access\-Datenbank \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)