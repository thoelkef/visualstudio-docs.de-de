---
title: Binden von Objekten in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9f410fdfea8a241b10cbab621dbd781d3648a080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="bind-objects-in-visual-studio"></a>Binden von Objekten in Visual Studio
Visual Studio bietet zur Entwurfszeit Tools zum Arbeiten mit benutzerdefinierten Objekten als Datenquelle in der Anwendung. Wenn Sie Daten aus einer Datenbank in einem Objekt zu speichern, die Sie an der UI-Steuerelemente binden möchten, ist die empfohlene Vorgehensweise Entity Framework verwendet, um die Klasse oder Klassen zu generieren. Entity Framework-generiert automatisch alle der änderungsnachverfolgung Standardcode, was bedeutet, dass alle Änderungen an den lokalen Objekten automatisch in die Datenbank beibehalten werden, wenn Sie für das Objekt DbSet AcceptChanges aufrufen. Weitere Informationen finden Sie unter [Dokumentation zu Entity Framework](https://ef.readthedocs.org/en/latest/).  
  
> [!TIP]
>  Die Ansätze zum objektbindung in diesem Artikel sollte nur angesehen werden, wenn die Anwendung bereits auf Datasets basiert. Diese Ansätze können auch verwendet werden, wenn Sie bereits vertraut sind mit Datasets, und die Daten, die Sie verarbeiten möchten, tabellarische und nicht zu komplex oder zu groß sind. Jetzt noch einfacher beispielsweise im Zusammenhang mit Laden von Daten direkt in Objekte mithilfe von "DataReader" und das manuelle Aktualisieren der Benutzeroberflächenautomatisierungs ohne die Datenbindung, finden Sie unter [erstellen eine einfachen datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
## <a name="object-requirements"></a>Objekt-Anforderungen  
 Die einzige Anforderung für benutzerdefinierte Objekte, die mit den Daten in Visual Studio-Entwurfstools arbeiten wird, dass das Objekt mindestens eine öffentliche Eigenschaft ist erforderlich.  
  
 Im Allgemeinen erfordern benutzerdefinierte Objekte keine aufgabenspezifische Schnittstellen, Konstruktoren oder Attribute, das als Datenquelle für eine Anwendung fungiert. Jedoch wenn Sie möchten, ziehen das Objekt aus der **Datenquellen** Fenster auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements und wenn das Objekt implementiert die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> -Schnittstelle, das Objekt muss ein Standardwert vorhanden sein der Konstruktor. Andernfalls, Visual Studio das Datenquellenobjekt kann nicht instanziiert werden, und es wird eine Fehlermeldung angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>Beispiele für die Verwendung von benutzerdefinierten Objekte als Datenquellen  
 Während es unzählige Möglichkeiten gibt, Ihre Anwendungslogik implementieren, wenn Sie als Datenquelle mit Objekten arbeiten, sind Datenbanken für SQL einige standard-Vorgänge, die so vereinfacht werden können, mithilfe der Visual Studio generierten TableAdapter-Objekten. Auf dieser Seite wird erläutert, wie diese Standardprozesse implementieren mit TableAdapters.It dient nicht als Leitfaden zum Erstellen der benutzerdefinierten Objekte. Beispielsweise führen Sie den folgenden Standardvorgängen unabhängig von der spezifischen Implementierung Ihrer Objekte oder der Anwendungslogik in der Regel aus:  
  
-   Laden von Daten in Objekte (in der Regel aus einer Datenbank).  
  
-   Erstellen eine typisierte Auflistung von Objekten.  
  
-   Objekte hinzufügen und Entfernen von Objekten aus einer Auflistung.  
  
-   Die Daten des Objekts wird für Benutzer in einem Formular angezeigt.  
  
-   Ändern Bearbeiten/der Daten in einem Objekt.  
  
-   Speichern von Daten aus Objekten in der Datenbank.   
  
### <a name="load-data-into-objects"></a>Laden Sie Daten in Objekten  
 In diesem Beispiel laden Sie Daten in die Objekte mithilfe von TableAdapters. Standardmäßig werden die TableAdapters mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abzurufen und Datentabellen auffüllen.  
  
-   Die `TableAdapter.Fill` Methode füllt eine vorhandene Datentabellen mit Daten zurückgegeben.  
  
-   Die `TableAdapter.GetData` Methode gibt eine neue Datentabelle mit Daten aufgefüllt.  
  
 Die einfachste Möglichkeit, benutzerdefinierte Objekte mit Daten zu laden, ist das Aufrufen der `TableAdapter.GetData` -Methode, durchlaufen Sie die Auflistung der Zeilen in der Tabelle zurückgegebenen Daten und füllen Sie jedes Objekt mit den Werten in jeder Zeile. Sie erstellen eine `GetData` Methode, die eine aufgefüllte Datentabelle für jede einem TableAdapter hinzugefügte Abfrage zurückgibt.  
  
> [!NOTE]
>  Visual Studio werden die TableAdapter-Abfragen `Fill` und `GetData` standardmäßig, aber diese Namen können in beliebiger gültiger Methodenname geändert werden.  
  
 Im folgende Beispiel wird gezeigt, wie zum Durchlaufen der Zeilen in einer Datentabelle und ein Objekt mit Daten aufgefüllt wird:  
  
 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### <a name="create-a-typed-collection-of-objects"></a>Erstellen Sie eine typisierte Auflistung von Objekten  
 Sie können Auflistungsklassen für Ihre Objekte erstellen oder verwenden Sie die typisierte Auflistungen, die automatisch von bereitgestellt werden die [BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component).  
  
 Wenn Sie eine benutzerdefinierte Auflistungsklasse für Objekte erstellen, es wird empfohlen, Sie erben <xref:System.ComponentModel.BindingList%601>. Diese generische Klasse stellt die Funktionalität zum Verwalten Ihrer Sammlung als auch die Möglichkeit zum Auslösen von Ereignissen, die Senden von Benachrichtigungen an die Infrastruktur der Datenbindung in Windows Forms bereit.  
  
 Die automatisch generierte Auflistung in der <xref:System.Windows.Forms.BindingSource> verwendet eine <xref:System.ComponentModel.BindingList%601> für die typisierte Auflistung. Wenn Ihre Anwendung erfordert keine zusätzliche Funktionalität, zum Verwalten können Sie der Auflistung innerhalb der <xref:System.Windows.Forms.BindingSource>. Weitere Informationen finden Sie unter der <xref:System.Windows.Forms.BindingSource.List%2A> Eigenschaft von der <xref:System.Windows.Forms.BindingSource> Klasse.  
  
> [!NOTE]
>  Wenn Ihre Sammlung nicht durch die grundlegende Implementierung der bereitgestellte Funktionalität erfordert die <xref:System.ComponentModel.BindingList%601>, damit Sie bei Bedarf auf die Klasse hinzufügen können, erstellen Sie eine benutzerdefinierte Sammlung sollte.  
  
 Der folgende Code zeigt, wie die Klasse für eine stark typisierte Auflistung von erstellt `Order` Objekte:  
  
 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### <a name="add-objects-to-a-collection"></a>Hinzufügen von Objekten zu einer Auflistung  
 Hinzufügen von Objekten zu einer Auflistung durch Aufrufen der `Add` Methode, die benutzerdefinierte Auflistungsklasse oder von der <xref:System.Windows.Forms.BindingSource>.  
  
 
> [!NOTE]
>  Die `Add` Methode wird automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.  
  
 Der folgende Code zeigt, wie Objekte in der typisierten Auflistung hinzufügen einer <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 Der folgende Code zeigt, wie eine typisierte Auflistung Objekte hinzu, die von erben <xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  In diesem Beispiel wird die `Orders` Auflistung ist eine Eigenschaft der `Customer` Objekt.  
  
 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### <a name="remove-objects-from-a-collection"></a>Entfernen von Objekten aus einer Auflistung  
 Entfernen von Objekten aus einer Auflistung durch Aufrufen der `Remove` oder `RemoveAt` Methode, die benutzerdefinierte Auflistungsklasse oder der <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Die `Remove` und `RemoveAt` Methoden werden automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.  
  
 Der folgende Code zeigt, wie zum Suchen und Entfernen von Objekten aus der typisierten Auflistung in ein <xref:System.Windows.Forms.BindingSource> mit der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> Methode:  
  
 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### <a name="display-object-data-to-users"></a>Object-Daten für Benutzer anzeigen  
 Um die Daten in Objekten für Benutzer anzuzeigen, erstellen Sie ein Objekt Datenquelle mithilfe der **Datenquellenkonfiguration** Assistenten, und ziehen Sie das gesamte Objekt oder die einzelnen Eigenschaften auf dem Formular aus dem **Datenquellen**Fenster.  
  
### <a name="modify-the-data-in-objects"></a>Ändern Sie die Daten in Objekten  
 Zum Bearbeiten von Daten in benutzerdefinierten Objekten, die Daten an Windows Forms-Steuerelemente gebunden werden, bearbeiten Sie einfach die Daten im gebundenen Steuerelement (oder direkt in die Eigenschaften des Objekts). Datenbindungsarchitektur werden die Daten in das Objekt aktualisiert.  
  
 Wenn Ihre Anwendung die nachverfolgung der Änderungen und Rollback vorgeschlagenen Änderungen auf ihre ursprünglichen Werte erfordert, müssen Sie diese Funktion in Ihrem Objektmodell implementieren. Beispiele wie Datentabellen nachverfolgen vorgeschlagenen Änderungen von, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, und <xref:System.Data.DataTable.GetChanges%2A>.  
  
### <a name="save-data-in-objects-back-to-the-database"></a>Speichern von Daten in Objekten in der Datenbank  
 Die Werte aus dem Objekt auf dem TableAdapter-DBDirect-Methoden übergeben, um Daten wieder in der Datenbank zu speichern.  
  
 Visual Studio erstellt DBDirect-Methoden, die direkt gegen die Datenbank ausgeführt werden können. Diese Methoden erfordern keine Datasets oder DataTable-Objekte.  
  
|TableAdapter-DBDirect-Methode|Beschreibung|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Fügt neue Datensätze zu einer Datenbank, sodass Sie die Werte einzelner Spalten als Methodenparameter übergeben.|  
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die Update-Methode nimmt ursprüngliche und die neue Spaltenwerte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz zu aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode wird auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank, ergreifen Sie hierzu eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|  
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank, basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|  
  
 Durchlaufen Sie die Auflistung von Objekten (z. B. mithilfe einer für die nächsten Schleife) zum Speichern von Daten aus einer Auflistung von Objekten aus. Mit dem TableAdapter-DBDirect-Methoden, um die Werte für jedes Objekt mit der Datenbank zu senden.  
  
 Das folgende Beispiel zeigt, wie Sie die `TableAdapter.Insert` DBDirect-Methode, um direkt in der Datenbank einen neuen Kunden hinzuzufügen:  
  
 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)