---
title: Datenbindung für benutzerdefinierte Objekte
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 09e3ad2cfc2690c27e4e26e51f6b40d7afd79f54
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586990"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Binden von Objekten als Datenquellen in Visual Studio

Visual Studio bietet Entwurfszeit Tools zum Arbeiten mit benutzerdefinierten Objekten als Datenquelle in Ihrer Anwendung. Wenn Sie Daten aus einer Datenbank in einem Objekt speichern möchten, das Sie an UI-Steuerelemente binden, empfiehlt es sich, Entity Framework zu verwenden, um die Klasse oder die Klassen zu generieren. Entity Framework den gesamten Code für die Änderungs Nachverfolgung automatisch generiert, was bedeutet, dass alle Änderungen an den lokalen Objekten automatisch in der Datenbank persistent gespeichert werden, wenn Sie "Accept Changes" für das dbset-Objekt aufzurufen. Weitere Informationen finden Sie unter [Entity Framework-Dokumentation](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Die Vorgehensweisen für die Objekt Bindung in diesem Artikel sollten nur berücksichtigt werden, wenn Ihre Anwendung bereits auf Datasets basiert. Diese Ansätze können auch verwendet werden, wenn Sie bereits mit Datasets vertraut sind und die Daten, die verarbeitet werden, tabellarisch und nicht zu komplex oder zu groß sind. Ein noch einfacheres Beispiel, das das direkte Laden von Daten in Objekte mithilfe eines DataReader und das manuelle Aktualisieren der Benutzeroberfläche ohne Datenbindung beinhaltet, finden [Sie unter Erstellen einer einfachen Daten Anwendung mithilfe von ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Objekt Anforderungen

Die einzige Anforderung für benutzerdefinierte Objekte, mit den Daten Entwurfs Tools in Visual Studio zu arbeiten, besteht darin, dass das Objekt mindestens eine öffentliche Eigenschaft benötigt.

Im Allgemeinen erfordern benutzerdefinierte Objekte keine bestimmten Schnittstellen, Konstruktoren oder Attribute, die als Datenquelle für eine Anwendung fungieren. Wenn Sie das Objekt jedoch aus dem **Datenquellen** Fenster auf eine Entwurfs Oberfläche ziehen möchten, um ein Daten gebundenes Steuerelement zu erstellen, und wenn das Objekt die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> Schnittstelle implementiert, muss das Objekt über einen Standardkonstruktor verfügen. Andernfalls kann Visual Studio das Datenquellen Objekt nicht instanziieren und zeigt einen Fehler an, wenn Sie das Element auf die Entwurfs Oberfläche ziehen.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Beispiele für die Verwendung von benutzerdefinierten Objekten als Datenquellen

Es gibt unzählige Möglichkeiten, Ihre Anwendungslogik beim Arbeiten mit Objekten als Datenquelle zu implementieren. für SQL-Datenbanken gibt es jedoch einige Standard Vorgänge, die durch die Verwendung der von Visual Studio generierten TableAdapter-Objekte vereinfacht werden können. Auf dieser Seite wird erläutert, wie diese Standardprozesse mithilfe von TableAdapters implementiert werden. Es ist nicht als Leitfaden für das Erstellen von benutzerdefinierten Objekten gedacht. Beispielsweise führen Sie in der Regel die folgenden Standard Vorgänge unabhängig von der spezifischen Implementierung Ihrer Objekte oder der Logik der Anwendung aus:

- Laden von Daten in Objekte (in der Regel aus einer Datenbank).

- Erstellen einer typisierten Auflistung von-Objekten.

- Hinzufügen von Objekten zu und Entfernen von Objekten aus einer Auflistung.

- Anzeigen der Objektdaten für Benutzer in einem Formular.

- Ändern/Bearbeiten der Daten in einem-Objekt.

- Daten werden aus Objekten wieder in der Datenbank gespeichert.

### <a name="load-data-into-objects"></a>Laden von Daten in Objekte

In diesem Beispiel laden Sie Daten mithilfe von TableAdapters in Ihre Objekte. Standardmäßig werden TableAdapters mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abrufen und Datentabellen auffüllen.

- Die `TableAdapter.Fill`-Methode füllt eine vorhandene Datentabelle mit den zurückgegebenen Daten.

- Die `TableAdapter.GetData`-Methode gibt eine neue Datentabelle zurück, die mit Daten aufgefüllt wird.

Die einfachste Möglichkeit zum Laden benutzerdefinierter Objekte mit Daten besteht darin, die `TableAdapter.GetData`-Methode aufzurufen, die Auflistung der Zeilen in der zurückgegebenen Datentabelle zu durchlaufen und jedes-Objekt mit den Werten in den einzelnen Zeilen aufzufüllen. Sie können eine `GetData` Methode erstellen, die eine aufgefüllte Datentabelle für jede Abfrage zurückgibt, die einem TableAdapter hinzugefügt wurde.

> [!NOTE]
> Visual Studio benennt die TableAdapter-Abfragen `Fill` und `GetData` standardmäßig, Sie können diese Namen jedoch in einen beliebigen gültigen Methodennamen ändern.

Im folgenden Beispiel wird gezeigt, wie Sie die Zeilen in einer Datentabelle durchlaufen und ein Objekt mit Daten auffüllen:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Erstellen einer typisierten Auflistung von Objekten

Sie können Auflistungs Klassen für Ihre Objekte erstellen oder die typisierten Auflistungen verwenden, die automatisch von der [BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component)bereitgestellt werden.

Wenn Sie eine benutzerdefinierte Auflistungs Klasse für-Objekte erstellen, empfiehlt es sich, von <xref:System.ComponentModel.BindingList%601>zu erben. Diese generische Klasse bietet Funktionen zum Verwalten Ihrer Auflistung sowie zum Senden von Ereignissen, die Benachrichtigungen an die Daten Bindungs Infrastruktur in Windows Forms senden.

Bei der automatisch generierten Auflistung im <xref:System.Windows.Forms.BindingSource> wird ein <xref:System.ComponentModel.BindingList%601> für die typisierte-Auflistung verwendet. Wenn Ihre Anwendung keine zusätzliche Funktionalität benötigt, können Sie Ihre Sammlung innerhalb der <xref:System.Windows.Forms.BindingSource>beibehalten. Weitere Informationen finden Sie in der <xref:System.Windows.Forms.BindingSource.List%2A>-Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Klasse.

> [!NOTE]
> Wenn Ihre Auflistung Funktionen erfordert, die nicht von der Basis Implementierung der <xref:System.ComponentModel.BindingList%601>bereitgestellt werden, sollten Sie eine benutzerdefinierte Sammlung erstellen, damit Sie Sie der Klasse nach Bedarf hinzufügen können.

Der folgende Code zeigt, wie die-Klasse für eine stark typisierte Auflistung von `Order`-Objekten erstellt wird:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Hinzufügen von Objekten zu einer Sammlung

Sie fügen einer Auflistung Objekte hinzu, indem Sie die `Add`-Methode der benutzerdefinierten Auflistungs Klasse oder des <xref:System.Windows.Forms.BindingSource>aufrufen.

> [!NOTE]
> Die `Add`-Methode wird automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, wenn Sie von <xref:System.ComponentModel.BindingList%601>erben.

Der folgende Code zeigt, wie der typisierten-Auflistung in einer <xref:System.Windows.Forms.BindingSource>-Objekte hinzugefügt werden:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Der folgende Code zeigt, wie Sie einer typisierten Auflistung Objekte hinzufügen, die von <xref:System.ComponentModel.BindingList%601>erbt:

> [!NOTE]
> In diesem Beispiel ist die `Orders` Auflistung eine Eigenschaft des `Customer` Objekts.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Entfernen von Objekten aus einer Sammlung

Sie entfernen Objekte aus einer Auflistung, indem Sie die `Remove`-oder `RemoveAt`-Methode der benutzerdefinierten Auflistungs Klasse oder <xref:System.Windows.Forms.BindingSource>aufrufen.

> [!NOTE]
> Wenn Sie von <xref:System.ComponentModel.BindingList%601>erben, werden die Methoden `Remove` und `RemoveAt` automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt.

Der folgende Code zeigt, wie Sie Objekte in einer <xref:System.Windows.Forms.BindingSource> mit der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>-Methode suchen und aus der typisierten Auflistung entfernen:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Anzeigen von Objektdaten für Benutzer

Um die Daten in Objekten für Benutzer anzuzeigen, erstellen Sie mithilfe des Assistenten zum **Konfigurieren von Daten** Quellen eine Objektdaten Quelle, und ziehen Sie dann das gesamte Objekt oder einzelne Eigenschaften aus dem **Datenquellen** Fenster auf das Formular.

### <a name="modify-the-data-in-objects"></a>Ändern der Daten in Objekten

Wenn Sie Daten in benutzerdefinierten Objekten bearbeiten möchten, die an Windows Forms Steuerelemente an Daten gebunden sind, bearbeiten Sie einfach die Daten im gebundenen Steuerelement (oder direkt in den Eigenschaften des Objekts). Die Daten Bindungs Architektur aktualisiert die Daten im-Objekt.

Wenn die Anwendung die Nachverfolgung von Änderungen und das Rollback der vorgeschlagenen Änderungen an ihren ursprünglichen Werten erfordert, müssen Sie diese Funktionalität in Ihrem Objektmodell implementieren. Beispiele für die Art und Weise, wie Datentabellen vorgeschlagene Änderungen verfolgen, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>und <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Daten in Objekten wieder in der Datenbank speichern

Speichern Sie die Daten wieder in der Datenbank, indem Sie die Werte aus dem-Objekt an die DBDirect-Methoden des TableAdapter übergeben.

Visual Studio erstellt DBDirect-Methoden, die direkt für die Datenbank ausgeführt werden können. Für diese Methoden sind keine Datasets oder Daten baren Objekte erforderlich.

|TableAdapter-DBDirect-Methode|Beschreibung|
| - |-----------------|
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu, sodass einzelne Spaltenwerte als Methoden Parameter übergeben werden können.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die Update-Methode nimmt die ursprünglichen und neuen Spaltenwerte als Methoden Parameter an. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden zum Aktualisieren dieses Datensatzes verwendet.<br /><br /> Die `TableAdapter.Update`-Methode wird auch verwendet, um Änderungen in einem Dataset an die Datenbank zurück zustimmen, indem eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>oder ein Array von <xref:System.Data.DataRow>s als Methoden Parameter verwendet wird.|
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank auf Grundlage der ursprünglichen Spaltenwerte, die als Methoden Parameter weitergegeben werden.|

Um Daten aus einer Auflistung von-Objekten zu speichern, durchlaufen Sie die Auflistung von-Objekten (z. b. mithilfe einer for-Next-Schleife). Senden Sie die Werte für jedes Objekt mithilfe der DBDirect-Methoden des TableAdapter an die Datenbank.

Im folgenden Beispiel wird gezeigt, wie die `TableAdapter.Insert` DBDirect-Methode verwendet wird, um einen neuen Kunden direkt der-Datenbank hinzuzufügen:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
