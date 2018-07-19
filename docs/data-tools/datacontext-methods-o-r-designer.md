---
title: DataContext-Methoden (O / R-Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d8e3a39c79b5dee339c8835c78143277f3015f6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756128"
---
# <a name="datacontext-methods-or-designer"></a>DataContext-Methoden (O/R-Designer)

<xref:System.Data.Linq.DataContext> Methoden (im Rahmen der [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) gibt Methoden, die <xref:System.Data.Linq.DataContext> -Klasse, die gespeicherten Prozeduren und Funktionen in einer Datenbank ausführen.

Die <xref:System.Data.Linq.DataContext>-Klasse ist eine [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klasse, die als Verbindung zwischen einer SQL Server-Datenbank und den [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Entitätsklassen dient, die dieser Datenbank zugeordnet sind. Die <xref:System.Data.Linq.DataContext>-Klasse enthält die Verbindungszeichenfolgeninformationen und die Methoden zum Herstellen einer Verbindung mit einer Datenbank und zum Ändern der Daten in der Datenbank. Standardmäßig enthält die <xref:System.Data.Linq.DataContext>-Klasse mehrere Methoden, die Sie aufrufen können, z. B. die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>-Methode, die aktualisierte Daten aus [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen an die Datenbank sendet. Sie können auch zusätzliche erstellen <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet. Das heißt, Aufrufen dieser benutzerdefinierten Methoden führt die gespeicherte Prozedur oder Funktion in der Datenbank, die <xref:System.Data.Linq.DataContext> Methode zugeordnet ist. Sie können der <xref:System.Data.Linq.DataContext>-Klasse neue Methoden hinzufügen, wie Sie auch anderen Klassen Methoden hinzufügen würden, um diese zu erweitern. Aber in Diskussionen zu <xref:System.Data.Linq.DataContext> Methoden im Rahmen der **O/R Designer**, ist die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen, die besprochen werden zugeordnet.

## <a name="methods-pane"></a>Methodenbereich

<xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet, werden angezeigt, der **Methoden** im Bereich der **O/R Designer**. Die **Methoden** ist der Bereich am Rand der **Entitäten** Bereich (der Hauptentwurfsoberfläche). Die **Methoden** Bereich listet alle <xref:System.Data.Linq.DataContext> Methoden, die Sie erstellt die **O/R Designer**. In der Standardeinstellung die **Methoden** Bereich leer ist, ziehen Sie gespeicherte Prozeduren oder Funktionen vom **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R-Designer**  erstellen <xref:System.Data.Linq.DataContext> Methoden, und füllen Sie die **Methoden** Bereich. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Öffnen und schließen Sie den Methodenbereich, mit der rechten Maustaste die **O/R Designer** , und klicken Sie dann auf **Methodenbereich ausblenden** oder **Methodenbereich anzeigen**, oder verwenden Sie die Tastenkombination  **STRG**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Zwei Typen von DataContext-Methoden

DataContext-Methoden sind Methoden, die gespeicherten Prozeduren und Funktionen in der Datenbank zugeordnet werden. Sie können das Erstellen und Hinzufügen von DataContext-Methoden auf die **Methoden** im Bereich der **O/R Designer**. Es gibt zwei unterschiedliche Arten von <xref:System.Data.Linq.DataContext> Methoden, die, die eine oder mehrere Resultsets zurückgeben und solche, die nicht der Fall ist:

-   <xref:System.Data.Linq.DataContext>-Methoden, die ein oder mehrere Resultsets zurückgeben:

     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung nur gespeicherte Prozeduren und Funktionen in der Datenbank ausführen und die Ergebnisse zurückgeben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, und <xref:System.Data.Linq.IMultipleResults>.

-   <xref:System.Data.Linq.DataContext>-Methoden, die keine Resultsets zurückgeben, wie Einfüge-, Update- und Löschvorgänge für eine bestimmte Entitätsklasse.

     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext> Methode, wenn die Anwendung, zum Ausführen von gespeicherter Prozeduren verfügt statt das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] -Standardverhalten zum Speichern geänderter Daten zwischen einer Entitätsklasse und der Datenbank. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Rückgabetypen von DataContext-Methoden

Beim Ziehen von gespeicherten Prozeduren und Funktionen von **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer**, der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode hängt davon ab, in dem Sie das Element ablegen. Die Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird erstellt eine <xref:System.Data.Linq.DataContext> -Methode mit dem Rückgabetyp der Entitätsklasse; durch Ablegen von Elementen in einem leeren Bereich des der **O/R Designer** (in beiden Bereichen) erstellt eine <xref:System.Data.Linq.DataContext> Methode die einen automatisch generierten Typ zurückgibt. Der automatisch generierte Typ hat es sich um den Namen, der mit übereinstimmt, die gespeicherte Prozedur oder den Funktionsnamen und die Eigenschaften, die die von der gespeicherten Prozedur oder Funktion zurückgegebenen Felder zuordnen.

> [!NOTE]
> Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder Ändern des Rückgabetyps des eine <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und überprüfen Sie die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Objekte, die Sie aus der Datenbank auf der O/R-Designer-Oberfläche ziehen heißen automatisch, basierend auf den Namen der Objekte in der Datenbank. Wenn Sie mehrere Male das gleiche Objekt ziehen, wird eine Zahl am Ende des neuen Namens hinzugefügt, die die Namen unterschieden. Wenn Namen von Datenbankobjekten Leerzeichen oder in Visual Basic oder C# nicht unterstützte Zeichen enthalten, wird das entsprechende Zeichen durch einen Unterstrich ersetzt.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Gespeicherte Prozeduren](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)