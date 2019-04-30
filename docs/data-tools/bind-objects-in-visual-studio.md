---
title: Datenbindung von benutzerdefinierten Objekten
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fb5a8c7a54871c7d948a458768c5551dbb5d550
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824363"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Binden von Objekten als Datenquellen in Visual Studio

Visual Studio bietet die Design-Time-Tools für die Arbeit mit benutzerdefinierten Objekten als Datenquelle in Ihrer Anwendung. Wenn Sie Daten aus einer Datenbank in einem Objekt zu speichern, die Sie an der UI-Steuerelemente binden möchten, wird empfohlen, Entity Framework verwenden, um die Klasse oder Klassen zu generieren. Entitätsframework-generiert automatisch alle änderungsnachverfolgung Codebausteine, was bedeutet, dass alle Änderungen an den lokalen Objekten automatisch in der Datenbank gespeichert werden, wenn Sie für das Objekt "DbSet" AcceptChanges aufrufen. Weitere Informationen finden Sie unter [Entity Framework-Dokumentation](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Die Ansätze zur Bindung von Objekten in diesem Artikel sollten nur berücksichtigt werden, wenn Ihre Anwendung bereits auf Datasets basiert. Sie können auch diese Ansätze verwenden, wenn Sie bereits mit Datasets vertraut sind, und die Daten, die Sie verarbeiten möchten tabellarisch und nicht zu komplex oder zu groß. Sogar noch einfacher beispielsweise im Zusammenhang mit Laden von Daten direkt in Objekte, indem Sie ein DataReader-Ziel und manuelles Aktualisieren der Benutzeroberflächenautomatisierungs ohne Datenbindung finden Sie unter [erstellen eine einfachen datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Objekt-Anforderungen

Die einzige Voraussetzung für benutzerdefinierte Objekte zum Arbeiten mit den Daten-Entwurfstools in Visual Studio ist, dass das Objekt mindestens eine öffentliche Eigenschaft benötigt.

Benutzerdefinierte Objekte erfordern im Allgemeinen keine bestimmte Schnittstellen, Konstruktoren oder Attribute, die als Datenquelle für eine Anwendung fungiert. Allerdings sollten Sie das Objekt aus ziehen die **Datenquellen** Fenster auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements, und wenn das Objekt implementiert die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> -Schnittstelle, das Objekt muss einen Standardwert aufweisen Konstruktor. Andernfalls, Visual Studio das Datenquellenobjekt kann nicht instanziiert werden, und es wird ein Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Beispiele für die Verwendung von benutzerdefinierter Objekten als Datenquellen

Es gibt unzählige Möglichkeiten, Ihre Anwendungslogik implementieren, wenn als Datenquelle mit Objekten arbeiten, sind Datenbanken für SQL einige standard-Vorgänge, die mit den Visual Studio generierten TableAdapter-Objekten vereinfacht werden können. Auf dieser Seite wird erläutert, wie Sie diese mithilfe von TableAdapters Standardprozesse implementieren. Es ist nicht als Leitfaden vorgesehen, für die Erstellung von benutzerdefinierten Objekten. Beispielsweise führen Sie die folgenden standard-Vorgänge unabhängig von der bestimmten Implementierung von den Objekten oder die Anwendungslogik in der Regel aus:

- Laden von Daten in Objekte (in der Regel aus einer Datenbank) aus.

- Erstellen eine typisierte Auflistung von Objekten.

- Objekte hinzufügen und Entfernen von Objekten aus einer Auflistung.

- Die Daten des Objekts wird für Benutzer in einem Formular angezeigt.

- Ändern Bearbeiten/der Daten in einem Objekt.

- Speichern von Daten aus Objekten in der Datenbank.

### <a name="load-data-into-objects"></a>Laden von Daten in Objekten

In diesem Beispiel laden Sie Daten in Ihre Objekte mit TableAdapters. Standardmäßig sind TableAdapters mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abzurufen und Datentabellen auffüllen.

- Die `TableAdapter.Fill` Methode füllt eine vorhandene Datentabellen mit den zurückgegebenen Daten.

- Die `TableAdapter.GetData` Methode gibt eine neue Datentabelle mit Daten aufgefüllt.

Die einfachste Möglichkeit zum Laden der benutzerdefinierten Objekte mit Daten aufrufen, wird die `TableAdapter.GetData` Methode, die die Auflistung der Zeilen in der Tabelle zurückgegebenen Daten durchlaufen und füllen Sie jedes Objekt mit den Werten in jeder Zeile. Sie erstellen eine `GetData` Methode, die eine aufgefüllte Datentabelle für jede einem TableAdapter hinzugefügte Abfrage zurückgibt.

> [!NOTE]
> Visual Studio werden die TableAdapter-Abfragen `Fill` und `GetData` standardmäßig, aber Sie können diesen Namen ändern, um einen beliebigen gültigen Methodennamen.

Das folgende Beispiel zeigt das Durchlaufen der Zeilen in einer Datentabelle und ein Objekt mit Daten aufzufüllen:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Erstellen Sie eine typisierte Auflistung von Objekten

Sie können für Ihre Objekte Auflistungsklassen zu erstellen oder verwenden Sie die typisierten Auflistungen, die automatisch von bereitgestellt werden die [BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component).

Wenn Sie eine benutzerdefinierte Auflistungsklasse für Objekte erstellen, es wird empfohlen, erben <xref:System.ComponentModel.BindingList%601>. Diese generische Klasse stellt Funktionen zum Verwalten Ihrer Sammlung als auch die Möglichkeit zum Auslösen von Ereignissen, die für das Senden von Benachrichtigungen an die Infrastruktur die Datenbindung in Windows Forms bereit.

Der automatisch generierte Auflistung in der <xref:System.Windows.Forms.BindingSource> verwendet eine <xref:System.ComponentModel.BindingList%601> für die typisierte Auflistung. Wenn Ihre Anwendung zusätzliche Funktionalität nicht erforderlich ist, verwaltet werden können die Auflistung innerhalb der <xref:System.Windows.Forms.BindingSource>. Weitere Informationen finden Sie unter den <xref:System.Windows.Forms.BindingSource.List%2A> Eigenschaft der <xref:System.Windows.Forms.BindingSource> Klasse.

> [!NOTE]
> Wenn Ihre Sammlung von die basisimplementierung für nicht bereitgestellte Funktionalität erfordert die <xref:System.ComponentModel.BindingList%601>, Sie sollten eine benutzerdefinierte Auflistung erstellen, sodass Sie auf die Klasse hinzufügen können, je nach Bedarf.

Der folgende Code zeigt, wie zum Erstellen der Klasse für eine stark typisierte Auflistung von `Order` Objekte:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Hinzufügen von Objekten zu einer Sammlung

Hinzufügen von Objekten zu einer Sammlung durch Aufrufen der `Add` Methode, die von einer benutzerdefinierten Auflistungsklasse oder die <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Die `Add` Methode wird automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.

Der folgende Code zeigt, wie Sie Objekte hinzufügen, der typisierte Sammlung in eine <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Der folgende Code zeigt, wie eine typisierte Auflistung Objekte hinzu, die von erbt <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> In diesem Beispiel die `Orders` Sammlung ist eine Eigenschaft der `Customer` Objekt.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Entfernen von Objekten aus einer Auflistung

Entfernen von Objekten aus einer Auflistung durch Aufrufen der `Remove` oder `RemoveAt` Methode, die von einer benutzerdefinierten Auflistungsklasse oder <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Die `Remove` und `RemoveAt` Methoden werden automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.

Der folgende Code zeigt, wie Suchen und Entfernen von Objekten aus der typisierten Auflistung in ein <xref:System.Windows.Forms.BindingSource> mit der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> Methode:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Objektdaten für Benutzer anzeigen

Um die Daten in Objekten auf Benutzer anzuzeigen, erstellen Sie ein Objekt Datenquelle mithilfe der **Datenquellenkonfiguration** Assistenten, und ziehen Sie dann das gesamte Objekt oder die einzelnen Eigenschaften auf das Formular aus der **Datenquellen**Fenster.

### <a name="modify-the-data-in-objects"></a>Ändern Sie die Daten in Objekten

Um Daten in benutzerdefinierten Objekten, die Daten an Windows Forms-Steuerelemente gebunden sind, zu bearbeiten, bearbeiten Sie einfach die Daten im gebundenen Steuerelement (oder direkt in die Eigenschaften des Objekts). Architektur zur Datenbindung aktualisiert die Daten in das Objekt.

Wenn Ihre Anwendung die nachverfolgung von Änderungen und Rollback vorgeschlagenen Änderungen auf ihre ursprünglichen Werte erfordert, müssen Sie diese Funktionalität in Ihrem Objektmodell implementieren. Beispiele wie Datentabellen vorgeschlagene Änderungen mitverfolgen, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, und <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Speichern von Daten in Objekten in der Datenbank

Speichern Sie Daten können Sie in der Datenbank, indem Sie die Werte aus dem Objekt auf dem TableAdapter-DBDirect-Methoden übergeben.

Visual Studio erstellt die DBDirect-Methoden, die direkt in der Datenbank ausgeführt werden können. Diese Methoden erfordern keine DataSet oder DataTable-Objekt.

|TableAdapter-DBDirect-Methode|Beschreibung|
| - |-----------------|
|`TableAdapter.Insert`|Fügt neue Datensätze zu einer Datenbank, sodass Sie die Werte einzelner Spalten als Methodenparameter übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die Update-Methode nimmt die ursprünglichen und neuen Werte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode wird auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank mithilfe einer <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|
|`TableAdapter.Delete`|Löscht den vorhandenen Datensätze aus der Datenbank, die basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|

Durchlaufen Sie die Auflistung von Objekten (z. B. mit einer for-Next-Schleife) zum Speichern von Daten aus einer Auflistung von Objekten aus. Mit dem TableAdapter-DBDirect-Methoden, um die Werte für jedes Objekt in der Datenbank zu senden.

Das folgende Beispiel zeigt, wie Sie mit der `TableAdapter.Insert` DBDirect-Methode zum Hinzufügen eines neuen Kunden direkt in der Datenbank:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)