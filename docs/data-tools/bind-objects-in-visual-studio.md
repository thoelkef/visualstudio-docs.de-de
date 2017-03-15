---
title: "Objektbindung in Visual&#160;Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Bindung, An Objekte"
  - "Daten [Visual Studio], Binden an Objekte"
  - "Daten [Visual Studio], Objektbindung"
  - "Objektbindung"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Objektbindung in Visual&#160;Studio
Visual Studio bietet Entwurfszeittools für die Arbeit mit benutzerdefinierten Objekten \(im Gegensatz zu anderen Datenquellen wie Entitäten, Datasets und Diensten\) als Datenquelle in der Anwendung.  
  
## Objektanforderungen  
 Bei benutzerdefinierten Objekten besteht die einzige Voraussetzung für die Zusammenarbeit mit Datenentwurfstools in Visual Studio darin, dass das Objekt mindestens eine öffentliche Eigenschaft enthalten muss.  
  
 Im Allgemeinen erfordern benutzerdefinierte Objekte keine speziellen Schnittstellen, Konstruktoren oder Attribute, um als Datenquelle für eine Anwendung zu fungieren.  Wenn Sie jedoch das Objekt vom Datenquellenfenster auf eine Entwurfsoberfläche ziehen möchten, um ein datengebundenes Steuerelement zu erstellen, und wenn das Objekt die <xref:System.ComponentModel.ITypedList>\-Schnittstelle oder die <xref:System.ComponentModel.IListSource>\-Schnittstelle implementiert, muss das Objekt über einen Standardkonstruktor verfügen \(das heißt, einen parameterlosen Konstruktor\).  Andernfalls kann Visual Studio das Datenquellenobjekt nicht instanziieren, und es wird ein Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.  
  
## Beispiele der Verwendung von benutzerdefinierten Objekte als Datenquellen  
 Beim Arbeiten mit Objekten als Datenquelle bestehen unzählige Möglichkeiten zum Implementieren der Anwendungslogik. Es gibt jedoch einige Standardvorgänge, die mit den von Visual Studio generierten [TableAdapter](../data-tools/tableadapter-overview.md)\-Objekten vereinfacht werden können.  Auf dieser Seite wird die Implementierung dieser Standardvorgänge mithilfe von TableAdapters beschrieben. Die Erläuterungen dienen jedoch nicht als Leitfaden zum Erstellen benutzerdefinierter Projekte.  So werden z. B. unabhängig von der jeweiligen Implementierung Ihrer Objekte oder der Anwendungslogik im Normalfall die folgenden Standardvorgänge ausgeführt:  
  
-   Laden von Daten in Objekte \(i. d. R. aus einer Datenbank\)  
  
-   Erstellen einer typisierten Auflistung von Objekten  
  
-   Hinzufügen von Objekten zu einer Auflistung und Entfernen der Objekte  
  
-   Anzeigen der Objektdaten für Benutzer in einem Formular  
  
-   Ändern bzw. Bearbeiten der in einem Objekt enthaltenen Daten  
  
-   Speichern der in einem Objekt enthaltenen Daten in die Datenbank  
  
> [!NOTE]
>  Um ein besseres Verständnis zu erzielen und einen Hintergrund zu den Beispielen auf dieser Seite zu erhalten, sollten Sie folgende exemplarische Vorgehensweise durcharbeiten: [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  In dieser exemplarischen Vorgehensweise werden die auf dieser Hilfeseite erläuterten Objekte erstellt.  
  
### Laden von Daten in Objekte  
 In diesem Beispiel laden Sie mit TableAdapters Daten in die Objekte.  TableAdapters werden standardmäßig mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abrufen und Datentabellen auffüllen.  
  
-   Die `TableAdapter.Fill`\-Methode füllt eine vorhandene Datentabelle mit den zurückgegebenen Daten auf.  
  
-   Die `TableAdapter.GetData`\-Methode gibt eine neue, mit Daten aufgefüllte Datentabelle zurück.  
  
 Der einfachste Weg zum Laden von Daten in die benutzerdefinierten Objekte besteht darin, die `TableAdapter.GetData`\-Methode aufzurufen, die Zeilenauflistung in der zurückgegebenen Datentabelle zu durchlaufen und jedes Objekt mit den Werten in der jeweiligen Zeile aufzufüllen.  Sie können eine `GetData`\-Methode erstellen, die für alle einem TableAdapter hinzugefügten Abfragen eine aufgefüllte Datentabelle zurückgibt.  
  
> [!NOTE]
>  In Visual Studio werden die TableAdapter\-Abfragen standardmäßig mit `Fill` und `GetData` bezeichnet, die Namen können jedoch durch einen beliebigen gültigen Methodennamen ersetzt werden.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie die Zeilen in einer Datentabelle durchlaufen und ein Objekt mit Daten auffüllen:  
  
 Ein vollständiges Codebeispiel finden Sie unter [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### Erstellen einer typisierten Auflistung von Objekten  
 Sie können für die Objekte Auflistungsklassen erstellen oder die typisierten Auflistungen verwenden, die automatisch über die [BindingSource\-Komponente](../Topic/BindingSource%20Component.md) bereitgestellt werden.  
  
 Für das Erstellen einer benutzerdefinierten Auflistungsklasse wird empfohlen, von <xref:System.ComponentModel.BindingList%601> zu erben.  Diese generische Klasse stellt Funktionen zum Verwalten der Auflistung sowie die Möglichkeit bereit, Ereignisse auszulösen, die Benachrichtigungen an die Datenbindungsinfrastruktur in Windows Forms senden.  
  
 Die automatisch generierte Auflistung in <xref:System.Windows.Forms.BindingSource> verwendet eine <xref:System.ComponentModel.BindingList%601>\-Klasse für die typisierte Auflistung.  Wenn die Anwendung keine zusätzlichen Funktionen erfordert, können Sie die Auflistung innerhalb von <xref:System.Windows.Forms.BindingSource> beibehalten.  Weitere Informationen finden Sie unter der <xref:System.Windows.Forms.BindingSource.List%2A>\-Eigenschaft der <xref:System.Windows.Forms.BindingSource>\-Klasse.  
  
> [!NOTE]
>  Wenn die Auflistung Funktionen erfordert, die von der Basisimplementierung der <xref:System.ComponentModel.BindingList%601>\-Klasse nicht bereitgestellt werden, müssen Sie eine benutzerdefinierte Auflistung erstellen, um der Klasse nach Bedarf Funktionen hinzufügen zu können.  
  
 Der folgende Code zeigt, wie die Klasse für eine stark typisierte Auflistung von `Order`\-Objekten erstellt wird:  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### Hinzufügen von Objekten zu einer Auflistung  
 Das Hinzufügen von Objekten zu einer Auflistung erfolgt durch den Aufruf der `Add`\-Methode der benutzerdefinierten Auflistungsklasse oder der <xref:System.Windows.Forms.BindingSource>.  
  
 Ein Beispiel für das Hinzufügen zu einer Auflistung mithilfe einer <xref:System.Windows.Forms.BindingSource> finden Sie unter der `LoadCustomers`\-Methode unter [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 Ein Beispiel für das Hinzufügen von Objekten zu einer benutzerdefinierten Auflistung finden Sie unter der `LoadOrders`\-Methode unter [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  Beim Erben von <xref:System.ComponentModel.BindingList%601> wird automatisch eine `Add`\-Methode für die benutzerdefinierte Auflistung bereitgestellt.  
  
 Der folgende Code zeigt, wie der typisierten Auflistung in einer <xref:System.Windows.Forms.BindingSource> Objekte hinzugefügt werden:  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 Der folgende Code zeigt, wie einer typisierten Auflistung Objekte hinzugefügt werden, die von <xref:System.ComponentModel.BindingList%601> erbt:  
  
> [!NOTE]
>  In diesem Beispiel ist die `Orders`\-Auflistung eine Eigenschaft des `Customer`\-Objekts.  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### Entfernen von Objekten aus einer Auflistung  
 Das Entfernen von Objekten aus einer Auflistung erfolgt durch den Aufruf der `Remove`\-Methode oder der `RemoveAt`\-Methode der benutzerdefinierten Auflistungsklasse oder der <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Beim Erben von <xref:System.ComponentModel.BindingList%601> werden automatisch eine `Remove`\-Methode und eine `RemoveAt`\-Methode für die benutzerdefinierte Auflistung bereitgestellt.  
  
 Der folgende Code zeigt, wie Objekte in einer <xref:System.Windows.Forms.BindingSource> gefunden und mithilfe der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>\-Methode entfernt werden:  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### Anzeigen von Objektdaten für Benutzer  
 Um Benutzern die in Objekten enthaltenen Daten anzuzeigen, erstellen Sie mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) eine Objektdatenquelle und ziehen anschließend das gesamte Objekt oder einzelne Eigenschaften aus dem **Datenquellenfenster** in das Formular.  
  
 Weitere Informationen zum Erstellen einer Objektdatenquelle finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Weitere Informationen zum Anzeigen der in Objekten enthaltenen Daten in Windows Forms finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
### Ändern der in Objekten enthaltenen Daten  
 Bearbeiten Sie in benutzerdefinierten Objekten enthaltene Daten, die an Windows Forms\-Steuerelemente gebunden sind, einfach im gebundenen Steuerelement \(oder direkt in den Eigenschaften des Objekts\).  Über die Datenbindungsarchitektur werden die Daten im Objekt aktualisiert.  
  
 Wenn die Anwendung das Verfolgen von Änderungen und das Rückgängigmachen vorgesehener Änderungen zur Wiederherstellung der ursprünglichen Werte erfordert, müssen Sie diese Funktionalität in Ihrem Objektmodell implementieren.  Beispiele dazu, wie Datentabellen vorgesehene Änderungen verfolgen, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> und unter <xref:System.Data.DataTable.GetChanges%2A>.  
  
### Zurückspeichern der in Objekten enthaltenen Daten in die Datenbank  
 Sie können Daten in die Datenbank zurückspeichern, indem Sie die im Objekt enthaltenen Werte an die DBDirect\-Methoden des TableAdapter übergeben.  
  
 Visual Studio erstellt DBDirect\-Methoden, die direkt an der Datenbank ausgeführt werden können.  Für diese Methoden ist kein DataSet\-Objekt oder DataTable\-Objekt erforderlich.  
  
|TableAdapter\-DBDirect\-Methode|Beschreibung|  
|-------------------------------------|------------------|  
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu, und ermöglicht die Übergabe einzelner Spaltenwerte als Methodenparameter.|  
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank.  Die Update\-Methode übernimmt die Werte der ursprünglichen und der neuen Spalte als Methodenparameter.  Anhand der ursprünglichen Werte wird der ursprüngliche Datensatz gefunden. Mit den neuen Werten wird dieser Datensatz anschließend aktualisiert.<br /><br /> Mit der `TableAdapter.Update`\-Methode werden auch Änderungen in einem Dataset abgeglichen, das an die Datenbank zurückgesendet wird. Dazu wird <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> oder ein Array aus <xref:System.Data.DataRow>s als Methodenparameter verwendet.|  
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank basierend auf den ursprünglichen Spaltenwerten, die als Methodenparameter übergeben werden.|  
  
 Um Daten aus einer Auflistung von Objekten zu speichern, durchlaufen Sie die Auflistung \(z. B. mit einer for\-next\-Schleife\), und übertragen Sie die Werte der einzelnen Objekte mithilfe der DBDirect\-Methode des TableAdapter in die Datenbank.  
  
 Im folgenden Beispiel wird gezeigt, wie ein neuer Kunde mithilfe der `TableAdapter.Insert`\-DBDirect\-Methode direkt der Datenbank hinzugefügt wird:  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## Siehe auch  
 [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Gewusst wie: Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Exemplarische Vorgehensweise: Speichern von Daten mit den TableAdapter\-DBDirect\-Methoden](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Speichern von Daten](../data-tools/saving-data.md)