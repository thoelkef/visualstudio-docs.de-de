---
title: Binden von Objekten
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee820bc246e11b722d663ecc6a6037f182bc2c33
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053116"
---
# <a name="bind-objects-in-visual-studio"></a>Binden von Objekten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bietet die Design-Time-Tools für die Arbeit mit benutzerdefinierten Objekten als Datenquelle in Ihrer Anwendung. Wenn Sie Daten aus einer Datenbank in einem Objekt zu speichern, die Sie an der UI-Steuerelemente binden möchten, wird empfohlen, Entity Framework verwenden, um die Klasse oder Klassen zu generieren. Entität Frameworkautogenerates alle änderungsnachverfolgung Codebausteine, was bedeutet, dass alle Änderungen an den lokalen Objekten automatisch in der Datenbank gespeichert werden, wenn Sie für das Objekt "DbSet" AcceptChanges aufrufen.    Weitere Informationen finden Sie unter [Entity Framework-Dokumentation](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Die Ansätze zur Bindung von Objekten in diesem Artikel sollten nur berücksichtigt werden, wenn Ihre Anwendung bereits auf Datasets basiert. Diese Ansätze können auch verwendet werden, wenn Sie bereits mit Datasets vertraut sind, und die Daten, die Sie verarbeiten möchten tabellarisch und nicht zu komplex oder zu groß. Sogar noch einfacher beispielsweise im Zusammenhang mit Laden von Daten direkt in Objekte, indem Sie ein DataReader-Ziel und manuelles Aktualisieren der Benutzeroberflächenautomatisierungs ohne Datenbindung finden Sie unter [erstellen eine einfachen datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Objekt-Anforderungen
 Die einzige Voraussetzung für benutzerdefinierte Objekte zum Arbeiten mit den Daten-Entwurfstools in Visual Studio ist, dass das Objekt mindestens eine öffentliche Eigenschaft benötigt.

 Benutzerdefinierte Objekte erfordern im Allgemeinen keine bestimmte Schnittstellen, Konstruktoren oder Attribute, die als Datenquelle für eine Anwendung fungiert. Allerdings sollten Sie das Objekt aus ziehen die **Datenquellen** Fenster auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements, und wenn das Objekt implementiert die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> -Schnittstelle, das Objekt muss einen Standardwert aufweisen Konstruktor. Andernfalls, Visual Studio das Datenquellenobjekt kann nicht instanziiert werden, und es wird ein Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Beispiele für die Verwendung von benutzerdefinierter Objekten als Datenquellen
 Es gibt unzählige Möglichkeiten, Ihre Anwendungslogik implementieren, wenn als Datenquelle mit Objekten arbeiten, sind Datenbanken für SQL einige standard-Vorgänge, die mit den Visual Studio – generierten TableAdapter-Objekten vereinfacht werden können. Auf dieser Seite wird erläutert, wie diese Standardprozesse implementieren mit TableAdapters.It dient nicht als Leitfaden zur Erstellung von benutzerdefinierten Objekten. Beispielsweise führen Sie die folgenden standard-Vorgänge unabhängig von der bestimmten Implementierung von den Objekten oder die Anwendungslogik in der Regel aus:

- Laden von Daten in Objekte (in der Regel aus einer Datenbank) aus.

- Erstellen eine typisierte Auflistung von Objekten.

- Objekte hinzufügen und Entfernen von Objekten aus einer Auflistung.

- Die Daten des Objekts wird für Benutzer in einem Formular angezeigt.

- Ändern Bearbeiten/der Daten in einem Objekt.

- Speichern von Daten aus Objekten in der Datenbank.

> [!NOTE]
>  Um besser zu verstehen, und geben den Kontext für die Beispiele auf dieser Seite, empfehlen wir, dass Sie die folgenden Aufgaben: [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Diese exemplarische Vorgehensweise erstellt, die hier besprochenen Objekte.

### <a name="loaddata-into-objects"></a>LoadData in Objekte
 In diesem Beispiel laden Sie Daten in Ihre Objekte mit TableAdapters. Standardmäßig sind TableAdapters mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abzurufen und Datentabellen auffüllen.

- Die `TableAdapter.Fill` Methode füllt eine vorhandene Datentabellen mit den zurückgegebenen Daten.

- Die `TableAdapter.GetData` Methode gibt eine neue Datentabelle mit Daten aufgefüllt.

  Die einfachste Möglichkeit zum Laden der benutzerdefinierten Objekte mit Daten aufrufen, wird die `TableAdapter.GetData` Methode, die die Auflistung der Zeilen in der Tabelle zurückgegebenen Daten durchlaufen und füllen Sie jedes Objekt mit den Werten in jeder Zeile. Sie erstellen eine `GetData` Methode, die eine aufgefüllte Datentabelle für jede einem TableAdapter hinzugefügte Abfrage zurückgibt.

> [!NOTE]
>  Visual Studio werden die TableAdapter-Abfragen `Fill` und `GetData` standardmäßig, aber diese Namen können in beliebiger gültiger Methodenname geändert werden.

 Das folgende Beispiel zeigt das Durchlaufen der Zeilen in einer Datentabelle und ein Objekt mit Daten aufzufüllen:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Erstellen Sie eine typisierte Auflistung von Objekten
 Sie können für Ihre Objekte Auflistungsklassen zu erstellen oder verwenden Sie die typisierten Auflistungen, die automatisch von bereitgestellt werden die [BindingSource-Komponente](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Wenn Sie eine benutzerdefinierte Auflistungsklasse für Objekte erstellen, es wird empfohlen, erben <xref:System.ComponentModel.BindingList%601>. Diese generische Klasse stellt Funktionen zum Verwalten Ihrer Sammlung als auch die Möglichkeit zum Auslösen von Ereignissen, die für das Senden von Benachrichtigungen an die Infrastruktur die Datenbindung in Windows Forms bereit.

 Die automatisch generierte Auflistung in der <xref:System.Windows.Forms.BindingSource> verwendet eine <xref:System.ComponentModel.BindingList%601> für die typisierte Auflistung. Wenn Ihre Anwendung erfordert keine zusätzliche Funktionalität, Sie können verwalten, die Auflistung innerhalb der <xref:System.Windows.Forms.BindingSource>. Weitere Informationen finden Sie unter den <xref:System.Windows.Forms.BindingSource.List%2A> Eigenschaft der <xref:System.Windows.Forms.BindingSource> Klasse.

> [!NOTE]
>  Wenn Ihre Sammlung von die basisimplementierung für nicht bereitgestellte Funktionalität erfordert die <xref:System.ComponentModel.BindingList%601>, Sie sollten eine benutzerdefinierte Auflistung erstellen, sodass Sie auf die Klasse hinzufügen können, je nach Bedarf.

 Der folgende Code zeigt, wie zum Erstellen der Klasse für eine stark typisierte Auflistung von `Order` Objekte:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects zu einer Sammlung
 Hinzufügen von Objekten zu einer Sammlung durch Aufrufen der `Add` Methode, die von einer benutzerdefinierten Auflistungsklasse oder die <xref:System.Windows.Forms.BindingSource>.

 Ein Beispiel für das Hinzufügen zu einer Sammlung mit einem <xref:System.Windows.Forms.BindingSource>, finden Sie unter den `LoadCustomers` -Methode in der [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Ein Beispiel des Hinzufügens von Objekten auf einer benutzerdefinierten Sammlung finden Sie unter den `LoadOrders` -Methode in der [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
>  Die `Add` Methode wird automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.

 Der folgende Code zeigt, wie Sie Objekte hinzufügen, der typisierte Sammlung in eine <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Der folgende Code zeigt, wie eine typisierte Auflistung Objekte hinzu, die von erbt <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  In diesem Beispiel die `Orders` Sammlung ist eine Eigenschaft der `Customer` Objekt.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Objekte aus einer Auflistung
 Entfernen von Objekten aus einer Auflistung durch Aufrufen der `Remove` oder `RemoveAt` Methode, die von einer benutzerdefinierten Auflistungsklasse oder <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  Die `Remove` und `RemoveAt` Methoden werden automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, beim erben von <xref:System.ComponentModel.BindingList%601>.

 Der folgende Code zeigt, wie Suchen und Entfernen von Objekten aus der typisierten Auflistung in ein <xref:System.Windows.Forms.BindingSource> mit der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> Methode:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>DisplayObject Daten für Benutzer
 Um die Daten in Objekten auf Benutzer anzuzeigen, erstellen Sie ein Objekt Datenquelle mithilfe der **Datenquellenkonfiguration** Assistenten, und ziehen Sie dann das gesamte Objekt oder die einzelnen Eigenschaften auf das Formular aus der **Datenquellen**Fenster.

### <a name="modify-the-data-in-objects"></a>Ändern Sie die Daten in Objekten
 Um Daten in benutzerdefinierten Objekten, die Daten an Windows Forms-Steuerelemente gebunden sind, zu bearbeiten, bearbeiten Sie einfach die Daten im gebundenen Steuerelement (oder direkt in die Eigenschaften des Objekts). Architektur zur Datenbindung aktualisiert die Daten in das Objekt.

 Wenn Ihre Anwendung die nachverfolgung von Änderungen und Rollback vorgeschlagenen Änderungen auf ihre ursprünglichen Werte erfordert, müssen Sie diese Funktionalität in Ihrem Objektmodell implementieren. Beispiele wie Datentabellen vorgeschlagene Änderungen mitverfolgen, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, und <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData in Objekten in der Datenbank
 Speichern Sie Daten können Sie in der Datenbank, indem Sie die Werte aus dem Objekt auf dem TableAdapter-DBDirect-Methoden übergeben.

 Visual Studio erstellt die DBDirect-Methoden, die direkt in der Datenbank ausgeführt werden können. Diese Methoden erfordern keine DataSet oder DataTable-Objekt.

|TableAdapter-DBDirect-Methode|Beschreibung|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Fügt neue Datensätze zu einer Datenbank, sodass Sie die Werte einzelner Spalten als Methodenparameter übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die Update-Methode nimmt die ursprünglichen und neuen Werte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode wird auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank mithilfe einer <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|
|`TableAdapter.Delete`|Löscht den vorhandenen Datensätze aus der Datenbank, die basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|

 Durchlaufen Sie die Auflistung von Objekten (z. B. mit einer for-Next-Schleife) zum Speichern von Daten aus einer Auflistung von Objekten aus. Mit dem TableAdapter-DBDirect-Methoden, um die Werte für jedes Objekt in der Datenbank zu senden.

 Das folgende Beispiel zeigt, wie Sie mit der `TableAdapter.Insert` DBDirect-Methode zum Hinzufügen eines neuen Kunden direkt in der Datenbank:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Siehe auch
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
