---
title: "&#220;bersicht &#252;ber TableAdapters | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DataAccessor"
  - "vbdata.Microsoft.VSDesigner.DataSource.DataAccessor"
  - "TableAdapter"
  - "vs.data.TableAdapter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Datasets"
  - "Daten [Visual Studio], TableAdapter"
  - "Daten [Visual Studio], TableAdapters"
  - "Abfragedaten in Visual Studio"
  - "TableAdapter"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
  - "TableAdapters"
  - "TableAdapters, Abfragen"
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# &#220;bersicht &#252;ber TableAdapters
TableAdapters ermöglichen die Kommunikation zwischen der Anwendung und einer Datenbank.  Dies bedeutet, dass ein TableAdapter eine Verbindung mit einer Datenbank herstellt, Abfragen oder gespeicherte Prozeduren ausführt und eine neue Datentabelle mit den zurückgegebenen Daten zurückgibt oder aber eine vorhandene <xref:System.Data.DataTable> mit den zurückgegebenen Daten füllt.  Mit TableAdapters werden außerdem aktualisierte Daten von der Anwendung an die Datenbank zurückgesendet.  
  
 Benutzer früherer Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] stellen sich einen TableAdapter am besten als <xref:System.Data.Common.DataAdapter> mit integriertem Verbindungsobjekt und der Möglichkeit vor, mehrere Abfragen aufzunehmen.  Jede einem TableAdapter hinzugefügte Abfrage wird als öffentliche Methode verfügbar gemacht, die wie jede andere Methode oder Funktion für ein Objekt aufgerufen wird.  
  
 Zusätzlich zur Standardfunktionalität eines <xref:System.Data.Common.DataAdapter> umfassen TableAdapters weitere typisierte Methoden zum Kapseln von Abfragen, die über ein gemeinsames Schema mit der zugeordneten typisierten <xref:System.Data.DataTable> verfügen.  Anders gesagt, ein TableAdapter kann beliebig viele Abfragen aufnehmen, solange diese Daten zurückgeben, die das gleiche Schema einhalten.  
  
 In der vorherigen Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden ADO.NET\-Datenadapter für die Kommunikation zwischen einer Anwendung und einer Datenbank verwendet.  Während Datenadapter immer noch eine Hauptkomponente von [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md) sind, sind TableAdapters mit dem Designer generierte Komponenten, die die Funktion von <xref:System.Data.Common.DataAdapter>s verbessern.  TableAdapters enthalten normalerweise die `Fill`\-Methode und die `Update`\-Methode, um Daten in einer Datenbank abzurufen und zu aktualisieren.  
  
 TableAdapters werden mit dem **Dataset\-Designer** innerhalb von Datasets mit starker Typisierung erstellt.  Sie können TableAdapters während der Erstellung eines neuen Datasets mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) erstellen.  Sie können TableAdapters auch in vorhandenen Datasets mit dem [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md) erstellen, oder Sie können Datenbankobjekte aus dem **Server\-Explorer** auf den **Dataset\-Designer** ziehen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Während TableAdapters mit dem **Dataset\-Designer** entworfen werden, werden die generierten TableAdapter\-Klassen nicht als geschachtelte <xref:System.Data.DataSet>\-Klassen generiert.  Sie befinden sich in einem separaten Namespace, der für jedes Dataset spezifisch ist.  Wenn Sie beispielsweise ein Dataset mit der Bezeichnung `NorthwindDataSet` besitzen, befinden sich die TableAdapters, die mit den im `NorthwindDataSet` enthaltenen <xref:System.Data.DataTable>s verknüpft sind, im `NorthwindDataSetTableAdapters`\-Namespace.  Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren.  Beispiel:  
  
 [!code-cs[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/tableadapter-overview_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/tableadapter-overview_1.vb)]  
  
## Zugeordnetes DataTable\-Schema  
 Wenn Sie einen TableAdapter erstellen, wird die ursprüngliche Abfrage oder gespeicherte Prozedur verwendet, um das Schema der <xref:System.Data.DataTable> zu definieren, die dem TableAdapter zugeordnet ist.  Sie führen diese anfängliche Abfrage oder gespeicherte Prozedur aus, indem Sie die `Fill`\-Hauptmethode des TableAdapter aufrufen \(wodurch die dem TableAdapter zugeordnete <xref:System.Data.DataTable> aufgefüllt wird\).  Alle Änderungen an der Hauptabfrage des TableAdapter spiegeln sich im Schema der zugeordneten Datentabelle wider.  Durch das Entfernen einer Spalte aus der Hauptabfrage wird z. B. auch die Spalte aus der zugeordneten Datentabelle entfernt.  Wenn in weiteren Abfragen des TableAdapter SQL\-Anweisungen verwendet werden, durch die Spalten zurückgegeben werden, die nicht in der Hauptabfrage enthalten sind, versucht der Designer, die Spaltenänderungen zwischen der Hauptabfrage und etwaigen zusätzlichen Abfragen zu synchronisieren.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten von TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md).  
  
## Aktualisierungsbefehle für TableAdapter  
 Die Aktualisierungsfunktionalität eines TableAdapter ist von der Menge der Informationen abhängig, die auf der Grundlage der im TableAdapter\-Assistenten enthaltenen Hauptabfrage verfügbar sind.  Beispielsweise sind TableAdapters, die so konfiguriert sind, dass sie Werte aus mehreren Tabellen \(JOINs\), Skalarwerte, Ansichten oder die Ergebnisse von Aggregatfunktionen abrufen, bei der Erstellung anfänglich nicht in der Lage, Aktualisierungen an die zugrunde liegende Datenbank zurückzusenden.  Sie können jedoch die Befehle INSERT, UPDATE und DELETE im **Eigenschaftenfenster** manuell konfigurieren.  
  
## TableAdapter\-Abfragen  
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Anders als Standarddatenadapter können TableAdapters mehrere Abfragen enthalten, um ihre zugeordneten Datentabellen aufzufüllen.  Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle.  Dadurch wird das Laden von Daten ermöglicht, die verschiedene Kriterien erfüllen.  Wenn die Anwendung beispielsweise eine Kundentabelle enthält, können Sie eine Abfrage erstellen, durch die die Tabelle mit allen Kunden aufgefüllt wird, deren Name mit einem bestimmten Buchstaben beginnt. Darüber hinaus können Sie eine weitere Abfrage erstellen, durch die die Tabelle mit allen Kunden aufgefüllt wird, die aus demselben Bundesland\/Kanton stammen.  Um eine `Customers`\-Tabelle mit Kunden in einem bestimmten Bundesland\/Kanton aufzufüllen, können Sie eine `FillByState`\-Abfrage erstellen, die als Parameter für den Wert für das Bundesland bzw. den Kanton Folgendes annimmt: `SELECT * FROM Customers WHERE State = @State`.  Sie führen die Abfrage aus, indem Sie die `FillByState`\-Methode aufrufen und den Parameterwert folgendermaßen übergeben: `CustomerTableAdapter.FillByState("WA")`.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Zusätzlich zu Abfragen, die Daten zurückgeben, die demselben Schema entsprechen wie die Datentabelle des TableAdapter, können Sie Abfragen hinzufügen, die \(einzelne\) Skalarwerte zurückgeben.  Beispielsweise ist das Erstellen einer Abfrage, die die Anzahl der Kunden zurückgibt \(`SELECT Count(*) From Customers`\) für einen `CustomersTableAdapter` gültig, obwohl die zurückgegebenen Daten nicht dem Schema der Tabelle entsprechen.  
  
## ClearBeforeFill\-Eigenschaft  
 Der TableAdapter fügt eine für die <xref:System.Data.Common.DataAdapter>\-Basisklasse nicht verfügbare Eigenschaft hinzu.  Jedes Mal, wenn Sie eine Abfrage zum Auffüllen der TableAdapter\-Datentabelle ausführen, werden die Daten standardmäßig gelöscht, und nur die Ergebnisse der Abfrage werden in die Tabelle geladen.  Legen Sie die `ClearBeforeFill`\-Eigenschaft des TableAdapter auf `false` fest, wenn Sie die von einer Abfrage zurückgegebenen Daten in die vorhandenen Daten in einer Datentabelle einfügen bzw. mit diesen zusammenführen möchten.  Unabhängig davon, ob Sie die Daten löschen, müssen Sie Aktualisierungen explizit an die Datenbank zurücksenden, wenn dies erforderlich ist.  Vergessen Sie also nicht, an den Daten in der Tabelle vorgenommene Änderungen zu speichern, bevor Sie eine weitere Abfrage zum Auffüllen der Tabelle ausführen.  Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## TableAdapter\-Vererbung  
 Durch TableAdapters wird die Funktionalität von Standarddatenadaptern erweitert, indem ein konfigurierter <xref:System.Data.Common.DataAdapter> gekapselt wird.  Standardmäßig erbt der TableAdapter von <xref:System.ComponentModel.Component> und kann nicht in die <xref:System.Data.Common.DataAdapter>\-Klasse umgewandelt werden.  Die Umwandlung eines TableAdapter in einen <xref:System.Data.Common.DataAdapter> führt zu einer <xref:System.InvalidCastException>.  Um die Basisklasse eines TableAdapter zu ändern, können Sie eine Klasse eingeben, die von der <xref:System.ComponentModel.Component> in der **Basisklassen**\-Eigenschaft des TableAdapter im **Dataset\-Designer** abgeleitet wird.  
  
## TableAdapter\-Methoden und \-Eigenschaften  
 Die TableAdapter\-Klasse ist nicht Bestandteil von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Daher sind in der Dokumentation und im **Objektkatalog** keine Informationen dazu zu finden.  Sie wird zur Entwurfszeit erstellt, wenn Sie einen der oben erwähnten Assistenten verwenden.  Der einem TableAdapter beim Erstellen zugewiesene Name basiert auf dem Namen der Tabelle, mit der Sie arbeiten.  Wenn Sie beispielsweise einen TableAdapter erstellen, der auf einer Tabelle basiert, die sich in einer Datenbank mit der Bezeichnung `Orders` befindet, erhält der TableAdapter den Namen `OrdersTableAdapter`.  Sie können den Klassennamen für den TableAdapter ändern, indem Sie die **Name**\-Eigenschaft im **Dataset\-Designer** verwenden.  
  
 Im Folgenden werden die gebräuchlichsten TableAdapter\-Methoden und \-Eigenschaften vorgestellt:  
  
|Member|Beschreibung|  
|------------|------------------|  
|`TableAdapter.Fill`|Füllt die dem TableAdapter zugeordnete Datentabelle mit den Ergebnissen des SELECT\-Befehls für den TableAdapter auf.  Weitere Informationen finden Sie unter [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Sendet Änderungen an die Datenbank zurück, und gibt eine der Anzahl der vom Aktualisierungsvorgang betroffenen Zeilen entsprechende ganze Zahl zurück.  Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Gibt eine neue mit Daten aufgefüllte <xref:System.Data.DataTable> zurück.|  
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Zeilen zu einer DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`\-Methoden aufrufen.|  
  
## TableAdapter\-Aktualisierungsmethode  
 TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle.  Die anfängliche `Fill`\-\(Haupt\-\)Abfrage des TableAdapter wird ebenso als Grundlage für die Erstellung des Schemas der zugeordneten Datentabelle verwendet wie die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand`, die der `TableAdapter.Update`\-Methode zugeordnet sind.  Dies bedeutet, dass beim Aufrufen der `Update`\-Methode für einen TableAdapter die Anweisungen ausgeführt werden, die bei der ursprünglichen TableAdapter\-Konfiguration erstellt wurden. Die zusätzlichen, mit dem **Konfigurations\-Assistenten für TableAdapter\-Abfragen** hinzugefügten Abfragen werden nicht ausgeführt.  
  
 Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Operationen mit den Befehlen aus, die Sie normalerweise ausführen würden.  Wenn Sie beispielsweise die `Fill`\-Methode für den Adapter aufrufen, führt der Adapter in seiner `SelectCommand`\-Eigenschaft einen Datenbefehl aus und verwendet einen Datenreader \(beispielsweise <xref:System.Data.SqlClient.SqlDataReader>\), um das Resultset in die Datentabelle zu laden.  Wenn Sie die `Update`\-Methode des Adapters aufrufen, wird entsprechend der zutreffende Befehl für jeden geänderten Datensatz in der Datentabelle ausgeführt \(in den Eigenschaften `UpdateCommand`, `InsertCommand` und `DeleteCommand`\).  
  
> [!NOTE]
>  Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt.  Wenn es sich bei der Hauptabfrage für den TableAdapter um mehr als eine SELECT\-Anweisung für eine einzelne Tabelle handelt, ist der Designer möglicherweise nicht in der Lage, die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` zu generieren.  Wenn diese Befehle nicht generiert werden, tritt beim Ausführen der `TableAdapter.Update`\-Methode möglicherweise ein Fehler auf.  
  
## TableAdapter GenerateDbDirectMethods  
 Zusätzlich zu den Befehlen `InsertCommand`, `UpdateCommand` und `DeleteCommand` werden für die TableAdapter\-Erstellung Methoden verwendet, die direkt gegen die Datenbank ausgeführt werden können.  Diese Methoden \(`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`\) können direkt aufgerufen werden, um Daten in der Datenbank zu bearbeiten.  Dies bedeutet, dass Sie zum Umgang mit Einfüge\-, Aktualisierungs\- und Löschvorgängen, die für die zugeordnete Datentabelle ausstehend sind, diese einzelnen Methoden vom Code aufrufen und dass nicht TableAdapter.Update aufgerufen wird.  
  
 Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die **GenerateDbDirectMethods**\-Eigenschaft des TableAdapter im **Eigenschaftenfenster** auf `false` fest.  Dem TableAdapter hinzugefügte zusätzliche Abfragen sind eigenständig und können diese Methoden nicht generieren.  
  
## TableAdapter\-Unterstützung für Typen mit Nullwert  
 Die TableAdapters unterstützen die Typen `Nullable(Of T)` und `T?`, für die ein NULL\-Wert zulässig ist.  Weitere Informationen zu Typen in Visual Basic, für die NULL\-Werte zulässig sind, finden Sie unter [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  Weitere Informationen zu Typen in C\#, für die NULL\-Werte zulässig sind, finden Sie unter [Verwenden von auf NULL festlegbaren Typen](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Datenbank \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)