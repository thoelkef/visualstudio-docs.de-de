---
title: "Arbeiten mit Datasets in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Cache [Visual Studio], Datasets"
  - "Berücksichtigung der Groß-/Kleinschreibung, Datasets"
  - "Untergeordnete Datensätze"
  - "Einschränkungen [Visual Basic], Datasets"
  - "Aktueller Datensatz im Dataset"
  - "Datenadapter, Auffüllen von Datasets"
  - "Datencaching, Datasets"
  - "Datenbeziehungen"
  - "Datenbanken [Visual Basic], Aktualisieren"
  - "DataRelation-Objekt, Datasets"
  - "DataSet-Klasse"
  - "DataSet-Klasse, Informationen über Datasets"
  - "Datasets [Visual Basic]"
  - "Datasets [Visual Basic], Erweiterte Eigenschaften"
  - "Datasets [Visual Basic], Füllen"
  - "Datasets [Visual Basic], msprop"
  - "Datasets [Visual Basic], namespace"
  - "Datasets [Visual Basic], Auffüllen"
  - "Datasets [Visual Basic], Beziehungen"
  - "Erweiterte Eigenschaften, In typisierten Datasets"
  - "Fremdschlüssel, Datasets"
  - "Master/Detail-Tabellen, Datasets"
  - "msprop"
  - "Übergeordnete Datensätze in Datasets"
  - "Verknüpfte Tabellen"
  - "Verknüpfte Tabellen, Datasets"
  - "Beziehungen, Datasets"
  - "Schemas [Visual Basic], Datasets"
  - "Typisierte Datasets"
  - "Typisierte Datasets, Im Vergleich zu nicht typisierten Datasets"
  - "Eindeutige Einschränkungen (Datasets)"
  - "Nicht typisierte Datasets"
  - "Nicht typisierte Datasets, Im Vergleich zu typisierten Datasets"
  - "Aktualisieren von Datasets, Informationen über Datasetaktualisierungen"
  - "XML [Visual Basic], Datasets"
  - "XML-Schemas, Informationen über XML-Schemas and Datasets"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arbeiten mit Datasets in Visual Studio
Datasets sind Objekte, die Datentabellen enthalten, in denen Sie die in einer Anwendung verwendeten Daten temporär speichern können.  Wenn die Anwendung mit Daten arbeiten muss, können Sie die dafür erforderlichen Daten in ein Dataset laden, womit für die Anwendung ein lokaler Datencache im Arbeitsspeicher bereitgestellt wird.  Die Arbeit mit den Daten in einem Dataset kann auch dann fortgesetzt werden, wenn die Anwendung von der Datenbank getrennt wird.  Das Dataset verwaltet die Informationen zu Datenänderungen, damit Aktualisierungen nachverfolgt und an die Datenbank zurückgesendet werden können, sobald die Anwendung erneut verbunden wird.  
  
 Die folgenden Themen enthalten Informationen zum Arbeiten mit Datasets in Visual Studio:  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)|Erläutert die Entwurfszeittools zum Erstellen von Datasets.|  
|[Gewusst wie: Erstellen eines typisierten Datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md)|Erläutert das Erstellen eines typisierten DataSets unter Verwendung von Entwurfstools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Gewusst wie: Erweitern der Funktionen eines Datasets](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|Erläutert die Schritte zum Erstellen einer partiellen Klasse für das Dataset, dem zusätzlich zu dem vom Designer generierten Code weiterer Code hinzugefügt werden kann.|  
|[Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|Erläutert, wie Sie über den **Projektmappen\-Explorer** und im **Datenquellenfenster** Datasets öffnen können.|  
|[Gewusst wie: Bearbeiten eines Datasets](../Topic/How%20to:%20Edit%20a%20Dataset.md)|Erläutert, wie Sie Objekte in einem Dataset mit dem **Dataset\-Designer** bearbeiten können.|  
|[Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet\-Designer](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|Enthält eine schrittweise Anleitung zum Erstellen eines typisierten Datasets ohne den **Assistenten zum Konfigurieren von Datenquellen**.|  
|[Entwerfen von DataTables](../data-tools/designing-datatables.md)|Enthält Links zu Themen, in denen erläutert wird, Sie mit Entwurfszeittools Datentabellen erstellen und bearbeiten können.|  
|[Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)|Enthält Links zu Themen, in denen erläutert wird, Sie mit Entwurfszeittools Datenbeziehungen erstellen und bearbeiten können.|  
|[TableAdapters](../Topic/TableAdapters.md)|Enthält Links zu Themen, in denen erläutert wird, Sie mit Entwurfszeittools TableAdapters erstellen und bearbeiten können.|  
|[Arbeiten mit Datasets in N\-Tier\-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)|Erklärt, worum es sich bei Anwendungen mit n Ebenen handelt und welche Funktionen für das Arbeiten mit Datasets in Anwendungen mit n Ebenen verfügbar sind.|  
  
 Die Struktur eines <xref:System.Data.DataSet> kann mit der Struktur einer relationalen Datenbank verglichen werden: Damit wird ein hierarchisches Objektmodell von Tabellen, Zeilen, Spalten, Einschränkungen und Beziehungen verfügbar gemacht.  
  
 Datasets sind entweder typisiert oder nicht typisiert.  \(Weitere Informationen finden Sie im Abschnitt unten mit dem Titel "Typisierte im Vergleich zu nicht typisierten Datasets"\). Typisierte Datasets leiten ihr Schema \(Tabellen\- und Spaltenstruktur\) von XSD\-Dateien ab und sind einfacher zu programmieren.  Sie können typisierte oder nicht typisierte Datasets in Ihren Anwendungen verwenden.  In Visual Studio gibt es jedoch mehr Tools für typisierte Datasets, und die Programmierung mit ihnen ist einfacher und weniger fehleranfällig.  
  
 Typisierte Datasets werden erstellt, indem der [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) ausgeführt wird oder indem im Menü **Projekt** über den Befehl **Neues Element hinzufügen** das **DataSet**\-Element hinzugefügt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines typisierten Datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
 Sie erstellen nicht typisierte Datasets, indem Sie **DataSet**\-Elemente aus der **Toolbox** auf den [Windows Forms Designer](http://msdn.microsoft.com/de-de/3c3d61f8-f36c-4d41-b9c3-398376fabb15) oder [Component Designer](../Topic/Component%20Designer.md) ziehen.  
  
 Bearbeiten Sie nach dem Erstellen die Datasets im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Sie erstellen und bearbeiten typisierte und nicht typisierte Datasets mithilfe der folgenden Teile des [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Namespace.  
  
 ![System.Data.DataSet&#45;Namespace](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
Datasets befinden sich im System.Data\-Namespace  
  
 Die Objekte eines Datasets werden über Standardprogrammierkonstrukte wie Eigenschaften und Auflistungen verfügbar gemacht.  Beispiele:  
  
-   Die <xref:System.Data.DataSet>\-Klasse enthält die <xref:System.Data.DataTableCollection>\-Auflistung mit Datentabellen und die <xref:System.Data.DataRelationCollection>\-Auflistung mit <xref:System.Data.DataRelation>\-Objekten.  
  
-   Die <xref:System.Data.DataTable>\-Klasse enthält die <xref:System.Data.DataRowCollection>\-Auflistung mit Tabellenzeilen, die <xref:System.Data.DataColumnCollection>\-Auflistung mit Datenspalten sowie die <xref:System.Data.DataTable.ChildRelations%2A>\-Auflistung und die <xref:System.Data.DataTable.ParentRelations%2A>\-Auflistung mit Datenbeziehungen.  
  
-   Die <xref:System.Data.DataRow>\-Klasse enthält die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft, deren Werte angeben, ob und wie die Zeile geändert wurde, seit die Datentabelle zum ersten Mal aus der Datenbank geladen wurde.  Zu den möglichen Werten für die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft zählen <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState>.  
  
## Auffüllen von Datasets mit Daten  
 Standardmäßig enthält ein Dataset eigentlich keine Daten.  Wenn ein Dataset mit Daten gefüllt wird, heißt das, dass Daten in die einzelnen <xref:System.Data.DataTable>\-Objekte geladen werden, aus denen das Dataset besteht.  Datentabellen werden gefüllt, indem TableAdapter\-Abfragen oder Befehle von Datenadaptern \(z. B. <xref:System.Data.SqlClient.SqlDataAdapter>\) ausgeführt werden.  Wenn Sie ein Dataset mit Daten füllen, werden verschiedene Ereignisse ausgelöst, die Einschränkungen werden überprüft usw.  Weitere Informationen zum Laden von Daten in ein Dataset finden Sie unter [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 Der Code, mit dem ein Dataset gefüllt wird, wird dem Ereignishandler für das Laden des Formulars hinzugefügt, wenn Sie Elemente aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf ein Formular in der Windows\-Anwendung ziehen.  Weitere Informationen erhalten Sie beim Abschließen der folgenden exemplarischen Vorgehensweise: [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
 Es folgt ein Beispiel für das Auffüllen eines Datasets mit einem TableAdapter:  
  
 [!code-cs[VbRaddataDatasets#1](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataDatasets#1](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_1.vb)]  
  
 Es gibt verschiedene Möglichkeiten, ein Dataset zu füllen:  
  
-   Wenn Sie das Dataset mit Entwurfszeittools erstellt haben, z. B. mit einem der Daten\-Assistenten, müssen Sie die `Fill`\-Methode eines TableAdapter aufrufen.  \(TableAdapters werden mit einer `Fill`\-Standardmethode erstellt. Sie können jedoch den Namen ändern, sodass der tatsächliche Methodenname anders lauten kann.\) Weitere Informationen finden Sie im Abschnitt "Füllen eines Datasets mithilfe eines TableAdapter" unter [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
-   Rufen Sie die `Fill`\-Methode eines <xref:System.Data.Common.DataAdapter> auf.  Weitere Informationen finden Sie unter [Auffüllen eines DataSet mit einem DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
-   Um die Tabellen im Dataset manuell aufzufüllen, erstellen Sie <xref:System.Data.DataRow>\-Objekte, und fügen Sie sie der <xref:System.Data.DataRowCollection>\-Auflistung der Tabelle hinzu.  \(Dies ist nur zur Laufzeit möglich. Zur Entwurfszeit kann die <xref:System.Data.DataRowCollection>\-Auflistung nicht festgelegt werden.\) Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einer 'DataTable'](../Topic/Adding%20Data%20to%20a%20DataTable.md).  
  
-   Lesen Sie ein XML\-Dokument oder einen XML\-Stream in das Dataset ein.  Weitere Informationen finden Sie unter der <xref:System.Data.DataSet.ReadXml%2A>\-Methode.  Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Einlesen von XML\-Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md).  
  
-   Führen Sie den Inhalt eines Datasets mit demjenigen eines anderen zusammen \(kopieren Sie ihn\).  Dieses Szenario ist hilfreich, wenn die Anwendung Datasets von verschiedenen Quellen \(z. B. verschiedenen XML\-Webdiensten\) erhält, sie jedoch in einem einzelnen Dataset konsolidieren muss.  Weitere Informationen finden Sie unter [Zusammenführen von DataSet\-Inhalten](../Topic/Merging%20DataSet%20Contents.md).  
  
-   Führen Sie den Inhalt einer <xref:System.Data.DataTable> mit demjenigen einer anderen zusammen \(kopieren Sie ihn\).  
  
## Speichern von in einem Dataset enthaltenen Daten in einer Datenbank  
 Wenn Änderungen an Datensätzen im Dataset vorgenommen werden, müssen diese Änderungen in die Datenbank zurückgeschrieben werden.  Um Änderungen aus dem Dataset in die Datenbank zu schreiben, rufen Sie die `Update`\-Methode des TableAdapter oder des <xref:System.Data.Common.DataAdapter> auf, der die Kommunikation zwischen dem Dataset und der zugehörigen Datenbank steuert.  
  
 Bei der Verwendung von Datenentwurfstools in Visual Studio senden Sie Daten zurück an eine Datenbank, indem Sie die Update\-Methode des TableAdapter aufrufen und die zu speichernde Datentabelle übergeben.  Beispiele:  
  
 [!code-cs[VbRaddataDatasets#2](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataDatasets#2](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_2.vb)]  
  
 Zur feineren Steuerung des Aktualisierungsvorgangs rufen Sie eine der DBDirect\-Methoden des TableAdapter auf, mit deren Hilfe Sie einzelne Werte für die einzelnen Datenzeilen übergeben können.  Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) und [Exemplarische Vorgehensweise: Speichern von Daten mit den TableAdapter\-DBDirect\-Methoden](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md).  
  
 Mit der <xref:System.Data.DataRow>\-Klasse werden einzelne Datensätze geändert. Sie enthält die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft, deren Werte angeben, ob und wie die Zeile geändert wurde, seit die Datentabelle zum ersten Mal aus der Datenbank geladen wurde.  Zu den möglichen Werten zählen <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState>.  Die `Update`\-Methoden des TableAdapter und des <xref:System.Data.Common.DataAdapter> untersuchen den Wert der <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft, um zu ermitteln, welche Datensätze in die Datenbank geschrieben werden müssen und welcher Datenbankbefehl \(`InsertCommand`, `UpdateCommand` oder `DeleteCommand`\) aufgerufen werden muss.  
  
 Weitere Informationen zum Aktualisieren von Daten finden Sie unter [Speichern von Daten](../data-tools/saving-data.md).  
  
## Navigieren in den Datensätzen von Datasets  
 Da ein Dataset ein vollständig separater Container für Daten ist, unterstützen Datasets \(im Gegensatz zu ADO\-Recordsets\) das Konzept eines aktuellen Datensatzes nicht.  Stattdessen sind alle Datensätze jederzeit im Dataset verfügbar.  
  
 Da es keinen aktuellen Datensatz gibt, gibt es auch keine bestimmte Eigenschaft, die auf einen aktuellen Datensatz zeigt. Außerdem gibt es keine Methoden oder Eigenschaften, um sich zwischen den Datensätzen zu bewegen \(siehe Hinweis unten\).  Sie können auf die einzelnen Tabellen im Dataset als Objekte zugreifen. Jede Tabelle macht eine Auflistung von Zeilen verfügbar.  Sie können diese wie eine beliebige Auflistung behandeln und über den Index der Auflistung auf die Zeilen zugreifen oder auflistungsspezifische Anweisungen in der Programmiersprache verwenden.  
  
 Beispielsweise können Sie die vierte Zeile der `Customers`\-Tabelle mit folgendem Code abrufen:  
  
 [!code-cs[VbRaddataDatasets#3](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataDatasets#3](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_3.vb)]  
  
> [!NOTE]
>  Wenn Sie Steuerelemente in einem Formular an ein Dataset binden, können Sie mithilfe der <xref:System.Windows.Forms.BindingNavigator>\-Komponente den Zugriff auf einzelne Datasets vereinfachen.  Weitere Informationen finden Sie unter [Gewusst wie: Navigieren durch Daten in Windows Forms](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md).  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] ermöglicht [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) für Daten in einem <xref:System.Data.DataSet>\-Objekt.  Weitere Informationen finden Sie unter [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Datasets und XML  
 Ein Dataset ist eine relationale Ansicht von Daten, die in XML dargestellt werden können.  Diese Beziehung ermöglicht es Ihnen, folgende Dataset\-Features zu nutzen.  
  
-   Die Struktur eines Datasets, also seine Tabellen, Spalten, Beziehungen und Einschränkungen, können in einem XML\-Schema definiert werden.  Datasets verwenden die Methoden <xref:System.Data.DataSet.ReadXmlSchema%2A> und <xref:System.Data.DataSet.WriteXmlSchema%2A>, um Schemas zu lesen und zu schreiben, in denen strukturierte Informationen gespeichert werden.  Wenn kein Schema verfügbar ist, kann das Dataset \(über die zugehörige <xref:System.Data.DataSet.InferXmlSchema%2A>\-Methode\) ein Schema aus den Daten in einem XML\-Dokument ableiten, das eine relationale Struktur aufweist.  Weitere Informationen zu XML\-Schemas finden Sie unter [Erstellen von XML\-Schemata](../Topic/Building%20XML%20Schemas.md).  
  
-   Sie können eine Datasetklasse generieren, die Schemainformationen zum Definieren der zugehörigen Datenstruktur enthält.  Ein solches Dataset wird als *typisiertes* Dataset bezeichnet.  Informationen zum Erstellen von typisierten Datasets finden Sie unter [Gewusst wie: Erstellen eines typisierten Datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Sie können ein XML\-Dokument oder einen XML\-Stream mit der <xref:System.Data.DataSet.ReadXml%2A>\-Methode des Datasets in das Dataset einlesen und ein Dataset mithilfe der <xref:System.Data.DataSet.WriteXml%2A>\-Methode des Datasets als XML schreiben.  Da XML ein Standardformat für den Datenaustausch zwischen verschiedenen Anwendungen ist, können Sie ein Dataset mit Daten im XML\-Format laden, das von anderen Anwendungen gesendet wurde.  Entsprechend kann ein Dataset seine Daten als XML\-Stream oder XML\-Dokument schreiben, damit sie mit anderen Anwendungen gemeinsam genutzt oder einfach in einem Standardformat gespeichert werden.  
  
-   Sie können eine XML\-Ansicht \(ein <xref:System.Xml.XmlDataDocument>\-Objekt\) vom Inhalt eines Datasets oder einer Datentabelle erstellen und die Daten anschließend mit einer relationalen Methode \(über das Dataset\) oder einer XML\-Methode anzeigen und bearbeiten.  Die beiden Ansichten werden automatisch synchronisiert, sobald Änderungen vorgenommen werden.  
  
## Typisierte und nicht typisierte Datasets  
 Ein typisiertes Dataset ist ein Dataset, das zuerst von der <xref:System.Data.DataSet>\-Basisklasse abgeleitet wird und das anschließend mithilfe von Informationen aus dem **Dataset\-Designer**, die in einer XSD\-Datei gespeichert sind, eine neue stark typisierte Datasetklasse generiert.  Informationen aus dem Schema \(Tabellen, Spalten usw.\) werden generiert und in diese neue **DataSet**\-Klasse als Gruppe von Objekten und Eigenschaften der ersten Klasse kompiliert.  Da ein typisiertes Dataset von der <xref:System.Data.DataSet>\-Basisklasse erbt, übernimmt die typisierte Klasse alle Funktionen der <xref:System.Data.DataSet>\-Klasse und kann mit Methoden verwendet werden, die eine Instanz einer <xref:System.Data.DataSet>\-Klasse als Parameter verwenden.  
  
 Ein nicht typisiertes Dataset besitzt dagegen kein entsprechendes integriertes Schema.  Wie ein typisiertes Dataset enthält auch ein nicht typisiertes Dataset Tabellen, Spalten usw., die allerdings nur als Auflistungen verfügbar gemacht werden.  \(Nachdem Sie die Tabellen und andere Datenelemente in einem nicht typisierten Dataset manuell erstellt haben, können Sie jedoch die Struktur des Datasets mit der <xref:System.Data.DataSet.WriteXmlSchema%2A>\-Methode des Datasets als Schema exportieren.\)  
  
### Unterschiede beim Datenzugriff in typisierten und nicht typisierten Datasets  
 Die Klasse für ein typisiertes Dataset verfügt über ein Objektmodell, in dem die zugehörigen Eigenschaften die tatsächlichen Namen der Tabellen und Spalten annehmen.  Wenn Sie mit einem typisierten Dataset arbeiten, können Sie mit folgendem Code auf eine Spalte verweisen. Beispiel:  
  
 [!code-cs[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_4.vb)]  
  
 Bei einem nicht typisierten Dataset verwenden Sie hingegen folgenden Code:  
  
 [!code-cs[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_5.vb)]  
  
 Der Zugriff auf typisierte Datasets ist nicht nur einfacher zu lesen, sondern wird auch vollständig von IntelliSense im **Code\-Editor** von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt.  Mit der Syntax für typisierte Datasets lässt es sich nicht nur einfacher arbeiten, sie gewährleistet auch die Typüberprüfung beim Kompilieren und reduziert dadurch erheblich die Fehlerquote beim Zuweisen von Werten zu Dataset\-Membern.  Wenn Sie den Namen einer Spalte im <xref:System.Data.DataSet> ändern und die Anwendung anschließend kompilieren, wird ein Buildfehler ausgegeben.  Wenn Sie in der **Aufgabenliste** auf den Buildfehler doppelklicken, gelangen Sie direkt zu der Codezeile oder den Codezeilen, in denen auf den alten Spaltennamen verwiesen wird.  Der Zugriff auf Tabellen und Spalten ist bei einem typisierten Dataset zur Laufzeit ebenfalls etwas schneller, da der Zugriff während des Kompilierens und nicht über Auflistungen zur Laufzeit bestimmt wird.  
  
 Typisierte Datasets bieten zwar viele Vorteile, in bestimmten Situationen sind nicht typisierte Datasets allerdings besser geeignet.  Dies ist eindeutig der Fall, wenn kein Schema für das Dataset vorhanden ist.  Dies kann beispielsweise vorkommen, wenn die Anwendung mit einer Komponente interagiert, die ein Dataset zurückgibt, dessen Struktur Sie aber nicht im Voraus kennen.  Es kann auch vorkommen, dass Sie mit Daten arbeiten, die keine statische, vorhersagbare Struktur aufweisen. In diesem Fall ist es unpraktisch, ein typisiertes Dataset zu verwenden, da Sie die Klasse des typisierten Datasets mit jeder Änderung in der Datenstruktur neu generieren müssten.  
  
 Häufig werden Sie ein Dataset dynamisch erstellen müssen, ohne dafür ein verfügbares Schema zu haben.  In diesem Fall bietet das Dataset einfach eine praktische Struktur zum Speichern von Informationen, so lange die Daten relational dargestellt werden können.  Gleichzeitig profitieren Sie von den Funktionen des Datasets, etwa der Möglichkeit, Informationen zu serialisieren, die an einen anderen Prozess weitergeleitet werden müssen, oder eine XML\-Datei zu schreiben.  
  
## Berücksichtigung der Groß\- und Kleinschreibung bei Datasets  
 In einem Dataset muss die Groß\- und Kleinschreibung bei Namen von Tabellen und Spalten standardmäßig nicht berücksichtigt werden, d. h. auf eine Tabelle im Dataset mit dem Namen "Customers" kann auch mit "customers" verwiesen werden. Dies entspricht den Benennungskonventionen in vielen Datenbanken, z. B. dem Standardverhalten von SQL Server, wonach die Namen von Datenelementen nicht ausschließlich anhand der Groß\- und Kleinschreibung unterschieden werden können.  
  
> [!NOTE]
>  Im Gegensatz zu Datasets spielt die Groß\- und Kleinschreibung bei XML\-Dokumenten eine Rolle, d. h. bei den Namen der in Schemas definierten Datenelemente muss die Groß\- und Kleinschreibung berücksichtigt werden.  Das Schemaprotokoll lässt es z. B. zu, dass in einem Schema eine Tabelle mit dem Namen "Customers" und eine weitere mit dem Namen "customers" definiert ist. Dies kann zu Namenskonflikten führen, wenn ein Schema mit Elementen, die sich nur durch die Groß\- und Kleinschreibung unterscheiden, zum Generieren einer Datasetklasse verwendet wird.  
  
 Die Groß\- bzw. Kleinschreibung kann sich jedoch auf die Interpretation von Daten im Dataset auswirken.  Wenn Sie beispielweise die Daten in einer Dataset\-Tabelle filtern, werden mit den Suchkriterien unter Umständen unterschiedliche Ergebnisse zurückgegeben, abhängig davon, ob für den Vergleich die Groß\- und Kleinschreibung berücksichtigt wird oder nicht.  Mit der <xref:System.Data.DataSet.CaseSensitive%2A>\-Eigenschaft eines Datasets steuern Sie, ob die Groß\- und Kleinschreibung beim Filtern, Suchen und Sortieren berücksichtigt werden soll.  Alle Tabellen im Dataset erben standardmäßig den Wert dieser Eigenschaft.  \(Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie die <xref:System.Data.DataTable.CaseSensitive%2A>\-Eigenschaft der Tabelle festlegen.\)  
  
## Verknüpfte Tabellen und DataRelation\-Objekte  
 Wenn es mehrere Tabellen in einem Dataset gibt, sind die Informationen in den Tabellen möglicherweise verknüpft.  Ein Dataset enthält keine inhärentes Informationen hinsichtlich solcher Beziehungen. Um mit Daten in verknüpften Tabellen arbeiten zu können, sollten Sie daher <xref:System.Data.DataRelation>\-Objekte erstellen, mit denen die Beziehungen zwischen den Tabellen im Dataset beschrieben werden.  Weitere Informationen finden Sie unter [Gewusst wie: Zugreifen auf Datensätze in verknüpften DataTables](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md).  Mit <xref:System.Data.DataRelation>\-Objekten können für einen übergeordneten Datensatz verknüpfte untergeordnete Datensätze sowie der übergeordnete Datensatz eines untergeordneten Datensatzes programmgesteuert abgerufen werden.  Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md).  Wenn Ihre Datenbank Beziehungen zwischen zwei oder mehr Tabellen enthält, werden die <xref:System.Data.DataRelation>\-Objekte automatisch durch die Entwurfstools erstellt.  
  
 Nehmen Sie als Beispiel Kunden\- und Auftragsdaten wie in der Northwind\-Datenbank.  Die `Customers`\-Tabelle kann z. B. folgende Datensätze enthalten:  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 Das Dataset könnte auch eine andere Tabelle mit Auftragsinformationen enthalten.  Die `Orders`\-Tabelle enthält eine Kunden\-ID als Fremdschlüsselspalte.  Wenn Sie nur einige Spalten in der `Orders`\-Tabelle auswählen, kann dies wie folgt aussehen:  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 Da es mehrere Aufträge pro Kunden geben kann, liegt eine 1:n\-Beziehung zwischen Kunden und Aufträgen vor.  In der Tabelle oben gibt es zwei Aufträge für den Kunden ALFKI.  
  
 Mit einem <xref:System.Data.DataRelation>\-Objekt können Sie die verknüpften Datensätze aus einer untergeordneten oder übergeordneten Tabelle abrufen.  Wenn Sie beispielsweise mit dem Datensatz für den Kunden ANTON arbeiten, wird die Auflistung der Datensätze abgerufen, aus denen die Aufträge für diesen Kunden hervorgehen.  Weitere Informationen finden Sie unter <xref:System.Data.DataRow.GetChildRows%2A>.  Wenn Sie mit dem Datensatz für OrderId 10507 arbeiten, können Sie auf ähnliche Weise im Beziehungsobjekt nach oben navigieren, um den Datensatz für das übergeordnete Element ANTON abzurufen.  Weitere Informationen finden Sie unter <xref:System.Data.DataRow.GetParentRow%2A>.  
  
## Einschränkungen  
 Wie in den meisten Datenbanken unterstützen Datasets Einschränkungen, um die Integrität von Daten sicherzustellen.  Einschränkungen sind Regeln, die beim Einfügen, Aktualisieren oder Löschen von Zeilen in einer Tabelle angewendet werden.  Sie können zwei Arten von Einschränkungen definieren:  
  
-   Eine *Unique*\-Einschränkung, die überprüft, ob die neuen Werte in einer Spalte in der Tabelle eindeutig sind.  
  
-   Eine *Fremdschlüssel*einschränkung, die Regeln dazu definiert, wie verknüpfte untergeordnete Datensätze aktualisiert werden sollen, wenn ein Datensatz in einer Mastertabelle aktualisiert oder gelöscht wird.  Durch eine Fremdschlüsseleinschränkung kann z. B. überprüft werden, ob ein übergeordneter Datensatz vorhanden ist, bevor das Erstellen untergeordneter Datensätze zugelassen wird.  
  
 In einem Dataset sind Einschränkungen mit einzelnen Tabellen \(Fremdschlüsseleinschränkungen\) oder mit Spalten \(eine Unique\-Einschränkung, die sicherstellt, dass Spaltenwerte einmalig sind\) verknüpft.  Einschränkungen werden als Objekte vom Typ <xref:System.Data.UniqueConstraint> oder <xref:System.Data.ForeignKeyConstraint> implementiert.  Anschließend werden sie zur <xref:System.Data.DataTable.Constraints%2A>\-Auflistung einer <xref:System.Data.DataTable> hinzugefügt.  Eine Unique\-Einschränkung kann auch auf andere Weise festgelegt werden, indem Sie einfach die <xref:System.Data.DataColumn.Unique%2A>\-Eigenschaft einer <xref:System.Data.DataColumn> auf `true` festlegen.  
  
 Das Dataset selbst unterstützt eine boolesche <xref:System.Data.DataSet.EnforceConstraints%2A>\-Eigenschaft, die angibt, ob Einschränkungen erzwungen werden oder nicht.  Diese Eigenschaft ist standardmäßig auf `true` festgelegt.  In manchen Situationen ist es jedoch sinnvoll, Einschränkungen vorübergehend zu deaktivieren.  Dies ist meistens dann der Fall, wenn Sie einen Datensatz so ändern, dass dies vorübergehend zu einem ungültigen Zustand führt.  Nachdem Sie die Änderung abgeschlossen haben \(und zum gültigen Zustand zurückgekehrt sind\), können Sie die Einschränkungen wieder aktivieren.  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellen Sie Einschränkungen implizit beim Definieren eines Datasets.  Wenn Sie einem Dataset einen Primärschlüssel hinzufügen, erstellen Sie implizit eine Unique\-Einschränkung für die Spalte mit dem Primärschlüssel.  Um für andere Spalten eine Unique\-Einschränkung anzugeben, legen Sie deren <xref:System.Data.DataColumn.Unique%2A>\-Eigenschaft auf `true` fest.  
  
 Eine Fremdschlüsseleinschränkung legen Sie fest, indem Sie ein <xref:System.Data.DataRelation>\-Objekt in einem Dataset erstellen.  Mithilfe eines <xref:System.Data.DataRelation>\-Objekts können Sie nicht nur programmgesteuert Informationen zu verknüpften Datensätzen abrufen, sondern auch Regeln für Fremdschlüsseleinschränkungen definieren.  
  
## Erweiterte Eigenschaften von Datasets  
 Erweiterte Eigenschaften stellen Namenszuordnungen bereit, wenn beim Generieren des Datasets aus einer XSD\-Datei Benennungskonflikte auftreten.  Wenn sich ein Bezeichner in der XSD\-Datei von dem berechneten Namen unterscheidet, der vom DataSet\-Generator erstellt wurde, wird dem Dataset im `msprop`\-Namespace eine erweiterte Eigenschaft hinzugefügt.  In der folgenden Tabelle werden die möglichen erweiterten Eigenschaften angezeigt, die generiert werden können:  
  
|Objekt|Erweiterte Eigenschaft|  
|------------|----------------------------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## Siehe auch  
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)