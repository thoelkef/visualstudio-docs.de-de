---
title: Objekte binden
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c487df5623a233146655593265e15c34a884de3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672998"
---
# <a name="bind-objects-in-visual-studio"></a>Binden von Objekten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bietet Entwurfszeit Tools zum Arbeiten mit benutzerdefinierten Objekten als Datenquelle in Ihrer Anwendung. Wenn Sie Daten aus einer Datenbank in einem Objekt speichern möchten, das Sie an UI-Steuerelemente binden, empfiehlt es sich, Entity Framework zu verwenden, um die Klasse oder die Klassen zu generieren. Entity frameworkautogeneriert den gesamten Code für die Änderungs Nachverfolgung, was bedeutet, dass alle Änderungen an den lokalen Objekten automatisch in der Datenbank persistent gespeichert werden, wenn Sie "Accept Changes" für das dbset-Objekt aufzurufen.    Weitere Informationen finden Sie unter [Entity Framework-Dokumentation](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Die Vorgehensweisen für die Objekt Bindung in diesem Artikel sollten nur berücksichtigt werden, wenn Ihre Anwendung bereits auf Datasets basiert. Diese Ansätze können auch verwendet werden, wenn Sie bereits mit Datasets vertraut sind und die Daten, die verarbeitet werden, tabellarisch und nicht zu komplex oder zu groß sind. Ein noch einfacheres Beispiel, das das direkte Laden von Daten in Objekte mithilfe eines DataReader und das manuelle Aktualisieren der Benutzeroberfläche ohne Datenbindung beinhaltet, finden [Sie unter Erstellen einer einfachen Daten Anwendung mithilfe von ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Objekt Anforderungen
 Die einzige Anforderung für benutzerdefinierte Objekte, mit den Daten Entwurfs Tools in Visual Studio zu arbeiten, besteht darin, dass das Objekt mindestens eine öffentliche Eigenschaft benötigt.

 Im Allgemeinen erfordern benutzerdefinierte Objekte keine bestimmten Schnittstellen, Konstruktoren oder Attribute, die als Datenquelle für eine Anwendung fungieren. Wenn Sie das Objekt jedoch aus dem **Datenquellen** Fenster auf eine Entwurfs Oberfläche ziehen möchten, um ein Daten gebundenes Steuerelement zu erstellen, und wenn das Objekt die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> Schnittstelle implementiert, muss das Objekt über einen Standardkonstruktor verfügen. Andernfalls kann Visual Studio das Datenquellen Objekt nicht instanziieren und zeigt einen Fehler an, wenn Sie das Element auf die Entwurfs Oberfläche ziehen.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Beispiele für die Verwendung von benutzerdefinierten Objekten als Datenquellen
 Es gibt unzählige Möglichkeiten, Ihre Anwendungslogik beim Arbeiten mit Objekten als Datenquelle zu implementieren. für SQL-Datenbanken gibt es jedoch einige Standard Vorgänge, die mithilfe der von Visual Studio – generierten TableAdapter-Objekte vereinfacht werden können. Auf dieser Seite wird erläutert, wie diese Standardprozesse mithilfe von TableAdapters.it implementiert werden, die nicht als Leitfaden zum Erstellen von benutzerdefinierten Objekten dienen. Beispielsweise führen Sie in der Regel die folgenden Standard Vorgänge unabhängig von der spezifischen Implementierung Ihrer Objekte oder der Logik der Anwendung aus:

- Laden von Daten in Objekte (in der Regel aus einer Datenbank).

- Erstellen einer typisierten Auflistung von-Objekten.

- Hinzufügen von Objekten zu und Entfernen von Objekten aus einer Auflistung.

- Anzeigen der Objektdaten für Benutzer in einem Formular.

- Ändern/Bearbeiten der Daten in einem-Objekt.

- Daten werden aus Objekten wieder in der Datenbank gespeichert.

> [!NOTE]
> Um die Beispiele auf dieser Seite besser zu verstehen und Kontext bereitzustellen, empfiehlt es sich, Folgendes auszuführen: Exemplarische Vorgehensweise [: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). In dieser exemplarischen Vorgehensweise werden die hier beschriebenen Objekte erstellt.

### <a name="loaddata-into-objects"></a>LoadData in Objekte
 In diesem Beispiel laden Sie Daten mithilfe von TableAdapters in Ihre Objekte. Standardmäßig werden TableAdapters mit zwei Arten von Methoden erstellt, die Daten aus einer Datenbank abrufen und Datentabellen auffüllen.

- Die `TableAdapter.Fill`-Methode füllt eine vorhandene Datentabelle mit den zurückgegebenen Daten.

- Die `TableAdapter.GetData`-Methode gibt eine neue Datentabelle zurück, die mit Daten aufgefüllt wird.

  Die einfachste Möglichkeit zum Laden benutzerdefinierter Objekte mit Daten besteht darin, die `TableAdapter.GetData`-Methode aufzurufen, die Auflistung der Zeilen in der zurückgegebenen Datentabelle zu durchlaufen und jedes-Objekt mit den Werten in den einzelnen Zeilen aufzufüllen. Sie können eine `GetData` Methode erstellen, die eine aufgefüllte Datentabelle für jede Abfrage zurückgibt, die einem TableAdapter hinzugefügt wurde.

> [!NOTE]
> Visual Studio benennt die TableAdapter-Abfragen `Fill` und `GetData` standardmäßig. diese Namen können jedoch in einen beliebigen gültigen Methodennamen geändert werden.

 Im folgenden Beispiel wird gezeigt, wie Sie die Zeilen in einer Datentabelle durchlaufen und ein Objekt mit Daten auffüllen:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Erstellen einer typisierten Auflistung von Objekten
 Sie können Auflistungs Klassen für Ihre Objekte erstellen oder die typisierten Auflistungen verwenden, die automatisch von der [BindingSource-Komponente](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)bereitgestellt werden.

 Wenn Sie eine benutzerdefinierte Auflistungs Klasse für-Objekte erstellen, empfiehlt es sich, von <xref:System.ComponentModel.BindingList%601> zu erben. Diese generische Klasse bietet Funktionen zum Verwalten Ihrer Auflistung sowie zum Senden von Ereignissen, die Benachrichtigungen an die Daten Bindungs Infrastruktur in Windows Forms senden.

 Die automatisch generierte Auflistung im <xref:System.Windows.Forms.BindingSource> verwendet eine <xref:System.ComponentModel.BindingList%601> für Ihre typisierte Auflistung. Wenn die Anwendung keine zusätzlichen Funktionen erfordert, können Sie Ihre Sammlung innerhalb der <xref:System.Windows.Forms.BindingSource> beibehalten. Weitere Informationen finden Sie in der <xref:System.Windows.Forms.BindingSource.List%2A>-Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Klasse.

> [!NOTE]
> Wenn Ihre Auflistung Funktionen erfordert, die nicht von der Basis Implementierung der <xref:System.ComponentModel.BindingList%601> bereitgestellt werden, sollten Sie eine benutzerdefinierte Sammlung erstellen, damit Sie Sie der Klasse nach Bedarf hinzufügen können.

 Der folgende Code zeigt, wie die-Klasse für eine stark typisierte Auflistung von `Order`-Objekten erstellt wird:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects zu einer Sammlung
 Sie fügen einer Auflistung Objekte hinzu, indem Sie die `Add`-Methode der benutzerdefinierten Auflistungs Klasse oder des <xref:System.Windows.Forms.BindingSource> aufrufen.

 Ein Beispiel für das Hinzufügen zu einer Auflistung mithilfe eines <xref:System.Windows.Forms.BindingSource> finden Sie in der `LoadCustomers`-Methode unter Exemplarische Vorgehensweise [: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Ein Beispiel für das Hinzufügen von Objekten zu einer benutzerdefinierten Auflistung finden Sie in der `LoadOrders`-Methode unter Exemplarische Vorgehensweise [: Herstellen einer Verbindung mit Daten in Objekten (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> Die `Add`-Methode wird automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt, wenn Sie von <xref:System.ComponentModel.BindingList%601> erben.

 Der folgende Code zeigt, wie der typisierten-Auflistung in einer <xref:System.Windows.Forms.BindingSource>-Objekte hinzugefügt werden:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Der folgende Code zeigt, wie Sie einer typisierten Auflistung Objekte hinzufügen, die von <xref:System.ComponentModel.BindingList%601> erbt:

> [!NOTE]
> In diesem Beispiel ist die `Orders` Auflistung eine Eigenschaft des `Customer` Objekts.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects aus einer Sammlung
 Sie entfernen Objekte aus einer Auflistung, indem Sie die `Remove`-oder `RemoveAt`-Methode der benutzerdefinierten Auflistungs Klasse oder <xref:System.Windows.Forms.BindingSource> aufrufen.

> [!NOTE]
> Wenn Sie von <xref:System.ComponentModel.BindingList%601> erben, werden die Methoden `Remove` und `RemoveAt` automatisch für Ihre benutzerdefinierte Sammlung bereitgestellt.

 Der folgende Code zeigt, wie Sie Objekte in einer <xref:System.Windows.Forms.BindingSource> mit der <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>-Methode suchen und aus der typisierten Auflistung entfernen:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Display Object-Daten für Benutzer
 Um die Daten in Objekten für Benutzer anzuzeigen, erstellen Sie mithilfe des Assistenten zum **Konfigurieren von Daten** Quellen eine Objektdaten Quelle, und ziehen Sie dann das gesamte Objekt oder einzelne Eigenschaften aus dem **Datenquellen** Fenster auf das Formular.

### <a name="modify-the-data-in-objects"></a>Ändern der Daten in Objekten
 Wenn Sie Daten in benutzerdefinierten Objekten bearbeiten möchten, die an Windows Forms Steuerelemente an Daten gebunden sind, bearbeiten Sie einfach die Daten im gebundenen Steuerelement (oder direkt in den Eigenschaften des Objekts). Die Daten Bindungs Architektur aktualisiert die Daten im-Objekt.

 Wenn die Anwendung die Nachverfolgung von Änderungen und das Rollback der vorgeschlagenen Änderungen an ihren ursprünglichen Werten erfordert, müssen Sie diese Funktionalität in Ihrem Objektmodell implementieren. Beispiele für die Art und Weise, wie Datentabellen vorgeschlagene Änderungen verfolgen, finden Sie unter <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> und <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData in Objekten zurück in die Datenbank
 Speichern Sie die Daten wieder in der Datenbank, indem Sie die Werte aus dem-Objekt an die DBDirect-Methoden des TableAdapter übergeben.

 Visual Studio erstellt DBDirect-Methoden, die direkt für die Datenbank ausgeführt werden können. Für diese Methoden sind keine Datasets oder Daten baren Objekte erforderlich.

|TableAdapter-DBDirect-Methode|Beschreibung|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu, sodass einzelne Spaltenwerte als Methoden Parameter übergeben werden können.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die Update-Methode nimmt die ursprünglichen und neuen Spaltenwerte als Methoden Parameter an. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden zum Aktualisieren dieses Datensatzes verwendet.<br /><br /> Die `TableAdapter.Update`-Methode wird auch verwendet, um Änderungen in einem Dataset an die Datenbank zurück zustimmen, indem eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> oder ein Array von <xref:System.Data.DataRow>s als Methoden Parameter verwendet wird.|
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank auf Grundlage der ursprünglichen Spaltenwerte, die als Methoden Parameter weitergegeben werden.|

 Um Daten aus einer Auflistung von-Objekten zu speichern, durchlaufen Sie die Auflistung von-Objekten (z. b. mithilfe einer for-Next-Schleife). Senden Sie die Werte für jedes Objekt mithilfe der DBDirect-Methoden des TableAdapter an die Datenbank.

 Im folgenden Beispiel wird gezeigt, wie die `TableAdapter.Insert` DBDirect-Methode verwendet wird, um einen neuen Kunden direkt der-Datenbank hinzuzufügen:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Siehe auch
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
