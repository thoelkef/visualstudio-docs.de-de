---
title: DataContext-Methoden (O-R-Designer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657391"
---
# <a name="datacontext-methods-or-designer"></a>DataContext-Methoden (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetid:///T: System. Data. Linq. DataContext? qualifyhint = false & AutoUpgrade = true)-Methoden (im Kontext der [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sind Methoden der <xref:System.Data.Linq.DataContext>-Klasse, die gespeicherte Prozeduren und Funktionen in einem ausführen. Verbindung.

 Die <xref:System.Data.Linq.DataContext>-Klasse ist eine [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klasse, die als Verbindung zwischen einer SQL Server-Datenbank und den [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Entitätsklassen dient, die dieser Datenbank zugeordnet sind. Die <xref:System.Data.Linq.DataContext>-Klasse enthält die Verbindungszeichenfolgeninformationen und die Methoden zum Herstellen einer Verbindung mit einer Datenbank und zum Ändern der Daten in der Datenbank. Standardmäßig enthält die <xref:System.Data.Linq.DataContext>-Klasse mehrere Methoden, die Sie aufrufen können, z. B. die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>-Methode, die aktualisierte Daten aus [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen an die Datenbank sendet. Sie können auch zusätzliche <xref:System.Data.Linq.DataContext>-Methoden erstellen, die gespeicherten Prozeduren und Funktionen zugeordnet werden. Mit anderen Worten: Durch das Aufrufen dieser benutzerdefinierten Methoden wird in der Datenbank die gespeicherte Prozedur oder die Funktion ausgeführt, der die <xref:System.Data.Linq.DataContext>-Methode zugeordnet ist. Sie können der <xref:System.Data.Linq.DataContext>-Klasse neue Methoden hinzufügen, wie Sie auch anderen Klassen Methoden hinzufügen würden, um diese zu erweitern. Bei Diskussionen über <xref:System.Data.Linq.DataContext> Methoden im Kontext der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sind jedoch die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet werden, die besprochen werden.

## <a name="methods-pane"></a>Methodenbereich
 Die gespeicherten Prozeduren und Funktionen zugeordneten <xref:System.Data.Linq.DataContext>-Methoden werden im Methodenbereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] angezeigt. Der Bereich Methoden ist der Bereich auf der Seite des Bereichs **Entitäten** (die Haupt Entwurfs Oberfläche). Im Methoden Bereich werden alle <xref:System.Data.Linq.DataContext> Methoden aufgelistet, die Sie mit der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] erstellt haben. Standardmäßig ist der Methoden Bereich leer. Ziehen Sie gespeicherte Prozeduren oder Funktionen aus **Server-Explorer** /**Datenbank-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], um <xref:System.Data.Linq.DataContext> Methoden zu erstellen und den Methoden Bereich aufzufüllen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Öffnen und schließen Sie den Bereich Methoden, indem Sie mit der rechten Maustaste auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] und dann auf **Methoden Bereich ausblenden** oder **Methoden Bereich anzeigen**klicken oder die Tastenkombination STRG + 1 verwenden.

## <a name="two-types-of-datacontext-methods"></a>Zwei Typen von DataContext-Methoden
 DataContext-Methoden sind Methoden, die gespeicherten Prozeduren und Funktionen in der Datenbank zugeordnet werden. DataContext-Methoden können im Methodenbereich des [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] erstellt und hinzugefügt werden. Es gibt zwei verschiedene Typen von <xref:System.Data.Linq.DataContext>-Methoden, die sich dadurch unterscheiden, dass von dem einen mindestens ein Resultset zurückgegeben wird und von dem anderen nicht:

- <xref:System.Data.Linq.DataContext>-Methoden, die ein oder mehrere Resultsets zurückgeben:

     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung nur gespeicherte Prozeduren und Funktionen in der Datenbank ausführen und die Ergebnisse zurückgeben muss. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult \<T > und <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext>-Methoden, die keine Resultsets zurückgeben, wie Einfüge-, Update- und Löschvorgänge für eine bestimmte Entitätsklasse.

     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung gespeicherte Prozeduren ausführen muss, statt das [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Standardverhalten zum Speichern geänderter Daten zwischen einer Entitätsklasse und der Datenbank zu verwenden. Weitere Informationen finden Sie unter Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktualisierungen, Einfügungen und Löschungen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Rückgabetypen von DataContext-Methoden
 Wenn Sie gespeicherte Prozeduren und Funktionen aus **Server-Explorer** /**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ziehen, unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode abhängig davon, wo Sie das Element ablegen. Wenn Sie die Elemente direkt auf einer vorhandenen Entitäts Klasse ablegen, wird eine <xref:System.Data.Linq.DataContext> Methode mit dem Rückgabetyp der Entitäts Klasse erstellt. Wenn Sie Elemente in einem leeren Bereich der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (in beiden Bereichen) ablegen, wird eine <xref:System.Data.Linq.DataContext> Methode erstellt, die einen automatisch generierten Typ zurückgibt. Der automatisch generierte Typ erhält einen Namen, der dem der gespeicherten Prozedur oder Funktion entspricht, und Eigenschaften, die den von der gespeicherten Prozedur oder Funktion zurückgegebenen Feldern entsprechen.

> [!NOTE]
> Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Rückgabe Typs einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Objekte, die von der Datenbank auf die Oberfläche des O/R-Designers gezogen werden, werden nach den Namen der Objekte in der Datenbank automatisch benannt. Wenn dasselbe Objekt mehrfach auf die Oberfläche gezogen wird, wird an das Ende des neuen Namens eine Nummer angehängt, damit die Namen unterschieden werden können. Wenn Namen von Datenbankobjekten Leerzeichen oder in Visual Basic oder C# nicht unterstützte Zeichen enthalten, wird das entsprechende Zeichen durch einen Unterstrich ersetzt.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [gespeicherte Prozeduren](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Aktualisierungen, einfügen und Löschungen (o/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Exemplarische Vorgehensweise [: Anpassen des Einfüge-, Aktualisierungs-und Lösch Verhaltens von Entitäts Klassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (o-r-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
