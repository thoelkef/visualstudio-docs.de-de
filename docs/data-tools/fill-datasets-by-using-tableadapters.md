---
title: "Auff&#252;llen von Datasets mit Daten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Daten [Visual Studio], Datasets"
  - "Daten [Visual Studio], Abrufen"
  - "Datenabruf"
  - "Datasets [Visual Basic]"
  - "Datasets [Visual Basic], Füllen"
  - "Datasets [Visual Basic], Laden von Daten"
  - "Abrufen von Daten"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Auff&#252;llen von Datasets mit Daten
Der TableAdapter stellt den typischen Mechanismus von Visual Studio zum Ausführen von Transact\-SQL\-Abfragen und zum Füllen von Datasets dar.  
  
 Sie können SQL\-Anweisungen oder gespeicherte Prozeduren mithilfe von TableAdapters oder Befehlsobjekten \(z. B. <xref:System.Data.SqlClient.SqlCommand>\) an einer Datenquelle ausführen.  Verwenden Sie TableAdapters, um Daten in Datasets zu laden, die mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwurfstools erstellt wurden.  Verwenden Sie Datenadapter, um Daten in Datasets zu laden, die programmgesteuert erstellt wurden.  Wenn die Anwendung keine Datasets verwendet, führen Sie SQL\-Anweisungen oder gespeicherte Prozeduren mithilfe von Befehlsobjekten direkt an einer Datenbank aus.  
  
 Die folgenden Themen enthalten Informationen zum Ausfüllen von Datasets mit Daten in Visual Studio:  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md)|Enthält Details, wie mithilfe von TableAdapters und DataAdapters Daten in Datasets geladen werden.|  
|[Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die Zeilen zurückgibt](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten SQL\-Anweisungen erstellt und ausgeführt werden, die Zeilen zurückgeben.|  
|[Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die einen einzelnen Wert zurückgibt](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten SQL\-Anweisungen erstellt und ausgeführt werden, die einzelne Werte zurückgeben.|  
|[Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die keinen Wert zurückgibt](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten SQL\-Anweisungen erstellt und ausgeführt werden, die keinen Wert zurückgeben.|  
|[Gewusst wie: Ausführen einer gespeicherten Prozedur, die Zeilen zurückgibt](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten gespeicherte Prozeduren ausgeführt werden, die Zeilen zurückgeben.|  
|[Gewusst wie: Ausführen einer gespeicherten Prozedur, die einen einzelnen Wert zurückgibt](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten gespeicherte Prozeduren ausgeführt werden, die einzelne Werte zurückgeben.|  
|[Gewusst wie: Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|Enthält Details, wie mithilfe von TableAdapter\-Abfragen und Command\-Objekten gespeicherte Prozeduren ausgeführt werden, die keinen Wert zurückgeben.|  
|[Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|Enthält Details zum Zuweisen von Werten zu Parametern in Abfragen und gespeicherten Prozeduren sowie zum Lesen von Werten in Parametern, die durch ausgeführte Befehle zurückgegeben werden.|  
|[Exemplarische Vorgehensweise: Füllen eines Datasets mit Daten](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|Enthält Details zum Erstellen eines Datasets und zum Auffüllen des Datasets mit Daten aus einer Datenbank.|  
|[Exemplarische Vorgehensweise: Einlesen von XML\-Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md)|Enthält Details zum Erstellen einer Windows\-Anwendung, die XML Daten in ein Dataset lädt und das Dataset anschließend in einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement anzeigt.|  
  
## Füllen von Datasets  
 Wenn Sie ein Dataset mit einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwurfszeittool \(z. B. [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md) oder [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)\) erstellen, verwenden Sie zum Füllen einen TableAdapter.  TableAdapter führen SQL\-Anweisungen und gespeicherte Prozeduren aus.  
  
 Wenn Sie ein Dataset ohne Entwurfszeittools erstellen, müssen Sie die Daten mithilfe von Datenadaptern füllen und aktualisieren.  \(TableAdapter stellen keine tatsächlichen Klassen in [.NET Framework 4.6 und 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md) dar. Demnach sind sie für die Arbeit mit Datasets, die ohne Entwurfszeittools erstellt wurden, nicht geeignet.\)  Weitere Informationen zum Laden von Daten in Datasets mittels TableAdapters oder Datenadapter finden Sie unter [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
## TableAdapter\-Abfragen  
 Sie können TableAdapter\-Abfragen ausführen, um Daten in Datasets zu füllen \(d. h. Daten in die DataTables zu laden, die ein Dataset bilden\).  TableAdapter\-Abfragen können mit dem [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) im **DataSet\-Designer** erstellt werden.  TableAdapter\-Abfragen treten als benannte Methoden für einen TableAdapter auf und werden durch Aufrufen der TableAdapter\-Methode ausgeführt.  Weitere Informationen zum Erstellen und Ausführen von TableAdapter\-Abfragen finden Sie auf den folgenden Seiten:  
  
-   [Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die Zeilen zurückgibt](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die einen einzelnen Wert zurückgibt](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [Gewusst wie: Erstellen und Ausführen einer SQL\-Anweisung, die keinen Wert zurückgibt](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [Gewusst wie: Ausführen einer gespeicherten Prozedur, die Zeilen zurückgibt](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [Gewusst wie: Ausführen einer gespeicherten Prozedur, die einen einzelnen Wert zurückgibt](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [Gewusst wie: Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## Befehlsobjekte  
 Mit Befehlsobjekten haben Sie die Möglichkeit, SQL\-Anweisungen und gespeicherte Prozeduren ohne <xref:System.Data.DataSet>, TableAdapter oder <xref:System.Data.Common.DataAdapter> direkt an einer Datenbank auszuführen.  \(Der Begriff *Befehlsobjekt* bezieht sich auf den speziellen Befehl für den .NET Framework\-Datenanbieter, der von der Anwendung verwendet wird.  Wenn in Ihrer Anwendung z. B. der .NET Framework\-Datenanbieter für SQL Server verwendet wird, lautet das Befehlsobjekt <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Befehle werden konfiguriert, um Daten mithilfe von SQL\-Anweisungen oder gespeicherten Prozeduren abzurufen. Dazu wird die `CommandType`\-Eigenschaft des Datenbefehls auf einen der Werte in der <xref:System.Data.IDbCommand.CommandType%2A>\-Enumeration festgelegt.  Legen Sie `CommandType` zum Ausführen von SQL\-Anweisungen auf <xref:System.Data.CommandType> fest, oder auf <xref:System.Data.CommandType>, um gespeicherte Prozeduren auszuführen.  Legen Sie die `CommandText`\-Eigenschaft anschließend entweder auf eine SQL\-Anweisung oder auf den Namen der gespeicherten Prozedur fest.  Danach können Sie den Datenbefehl ausführen, indem Sie eine seiner Execute\-Methoden aufrufen \(`ExecuteReader`, `ExecuteScalar`, `ExecuteNonQuery`\).  
  
 Jeder [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md) stellt ein Befehlsobjekt zur Verfügung, das für bestimmte Datenbanken optimiert wurde.  
  
 Datenbefehle ermöglichen Ihnen folgende Operationen in Ihrer Anwendung:  
  
-   Ausführen von **Select**\-Befehlen, die ein Ergebnis zurückgeben, das Sie direkt lesen können, statt es in das Dataset zu laden.  Verwenden Sie einen Datenreader \(<xref:System.Data.OleDb.OleDbDataReader>\-, <xref:System.Data.SqlClient.SqlDataReader>\-, <xref:System.Data.Odbc.OdbcDataReader>\- oder <xref:System.Data.OracleClient.OracleDataReader>\-Objekt\), um die Ergebnisse zu lesen. Der Datenreader verhält sich wie ein schreibgeschützter Vorwärtscursor, an den Sie Steuerelemente binden können.  Diese Strategie eignet sich zum Verringern der Speicherauslastung und zum sehr schnellen Laden von schreibgeschützten Daten.  
  
-   Ausführen von DDL\-Befehlen zum Erstellen, Bearbeiten und Entfernen von Tabellen, gespeicherten Prozeduren und anderen Datenbankstrukturen.  \(Für diese Aktionen benötigen Sie natürlich die entsprechenden Zugriffsrechte.\)  
  
-   Ausführen von Befehlen zum Abrufen von Kataloginformationen einer Datenbank.  
  
-   Ausführen dynamischer SQL\-Befehle zum Aktualisieren, Einfügen oder Löschen von Datasets anstelle des Aktualisierens von Tabellen im Dataset und des anschließenden Kopierens der Änderungen in die Datenbank.  
  
-   Ausführen von Befehlen, die einen Skalarwert \(d. h. einen einzelnen Wert\) zurückgeben, z. B. die Ergebnisse einer Aggregatfunktion \(SUM, COUNT, AVG usw.\).  
  
-   Ausführen von Befehlen, die Daten aus einer SQL Server\-Datenbank \(Version 7.0 oder höher\) im XML\-Format zurückgeben.  Typisches Anwendungsbeispiel: Ausführen einer Anfrage und Abrufen der Daten im XML\-Format, Durchführen einer XSLT\-Transformation \(zum Konvertieren ins HTML\-Format\) und Senden der Ergebnisse an einen Browser.  
  
 Die Eigenschaften eines Befehls enthalten alle erforderlichen Informationen, die für die Ausführung eines Befehls an einer Datenbank erforderlich sind.  Dies umfasst Folgendes:  
  
-   **Eine Verbindung** Der Befehl verweist auf eine Verbindung, über die er mit der Datenbank kommuniziert.  
  
-   **Der Name oder Text eines Befehls** Der Befehl enthält den eigentlichen Text einer SQL\-Anweisung oder den Namen einer auszuführenden gespeicherten Prozedur.  
  
-   **Parameter** Möglicherweise müssen Sie Parameterwerte zusammen mit dem Befehl übergeben \(Eingabeparameter\).  Der Befehl kann auch Werte in Form eines Rückgabewerts oder in Form von Ausgabeparameterwerten zurückgeben.  Zu jedem Befehl gehört eine bestimmte Anzahl von Parametern, die Sie einzeln festlegen oder lesen können, um Werte zu übergeben oder zu empfangen.  Weitere Informationen finden Sie unter [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Befehle werden mithilfe einer Methode ausgeführt, die sich für die erwarteten Ergebnisse eignet.  Wenn Sie z. B. Zeilen erwarten, rufen Sie die `ExecuteReader`\-Methode des Befehls auf, die Datensätze in einem Datenreader zurückgibt.  Wenn Sie einen UPDATE\-Befehl, einen INSERT\-Befehl oder einen DELETE\-Befehl ausführen, rufen Sie die `ExecuteNonQuery`\-Methode des Befehls auf, die einen Wert mit der Anzahl der betroffenen Zeilen zurückgibt.  Wenn Sie eine Aggregatfunktion \(z. B. Rückgabe der Anzahl an Bestellungen eines Kunden\) ausführen, rufen Sie die `ExecuteScalar`\-Methode auf.  
  
### Mehrere Resultsets  
 Befehlsobjekte werden z. B. verwendet, wenn eine einzelne Datentabelle \(eine Gruppe von Zeilen\) zurückgegeben werden soll.  Allerdings können Befehle Prozeduren ausführen, die mehrere Resultsets zurückgeben.  Dies kann sich auf verschiedene Arten vollziehen.  Eine Möglichkeit besteht darin, dass der Befehl auf eine gespeicherte Prozedur verweist, die mehrere Resultsets zurückgibt.  Alternativ dazu kann der Befehl auch zwei \(oder mehr\) Anweisungen oder Namen von gespeicherten Prozeduren enthalten.  In diesem Fall werden die Anweisungen oder Prozeduren nacheinander ausgeführt und mit einem einzelnen Aufruf mehrere Resultsets zurückgegeben.  
  
 Wenn Sie für einen Befehl mehrere Anweisungen oder Prozeduren festlegen, müssen diese alle vom selben Typ sein.  Sie können z. B. aufeinander folgende SQL\-Anweisungen oder aufeinander folgende gespeicherte Prozeduren ausführen.  Sie können jedoch nicht Aufrufe für gespeicherte Prozeduren und SQL\-Anweisungen im selben Befehl verwenden.  Weitere Informationen finden Sie unter [Abrufen von Daten mit einem DataReader](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md).  
  
> [!NOTE]
>  Bei Oracle\-Datenbanken unterstützt der .NET Framework\-Datenanbieter für Oracle keine als Batch verarbeitete SQL\-Anweisungen.  Er ermöglicht jedoch die Verwendung mehrerer REF CURSOR\-Ausgabeparameter, um ein Dataset in einer jeweils eigenen Datentabelle auszufüllen.  Sie müssen die Parameter definieren, diese als Ausgabeparameter markieren und angeben, dass sie REF CURSOR\-Datentypen sind.  Beachten Sie, dass Sie die `Update`\-Methode nicht verwenden können, wenn das <xref:System.Data.OracleClient.OracleDataAdapter>\-Objekt von REF CURSOR\-Parametern in eine gespeicherte Prozedur gefüllt wird. Dies liegt daran, dass Oracle\-Datenbanken nicht die Informationen bereitstellen, die beim Ausführen der SQL\-Anweisung erforderlich sind, um den Tabellennamen und die Spaltennamen festzustellen.  
  
## Sicherheit  
 Wenn Datenbefehle in Verbindung mit einer `CommandType`\-Eigenschaft verwendet werden, die auf <xref:System.Data.CommandType> festgelegt ist, müssen Sie die von einem Client gesendeten Informationen sorgfältig prüfen, bevor Sie sie an die Datenbank übergeben.  Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL\-Anweisungen zu senden \(einzufügen\), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen.  Bevor Sie Benutzereingaben an eine Datenbank übergeben, müssen Sie immer die Zulässigkeit der Informationen überprüfen.  Es wird empfohlen, möglichst immer parametrisierte Abfragen oder gespeicherte Prozeduren zu verwenden.  
  
## Siehe auch  
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Tools zum Arbeiten mit Datenquellen in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)