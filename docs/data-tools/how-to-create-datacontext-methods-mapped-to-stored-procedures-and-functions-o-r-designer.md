---
title: 'Vorgehensweise: Erstellen von DataContext-Methoden zugeordnet werden, um gespeicherte Prozeduren und Funktionen (O-R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6d086157761bbade92e7b79973876d18bc52f2fd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Vorgehensweise: Erstellen von DataContext-Methoden zugeordnet werden, um gespeicherte Prozeduren und Funktionen (O/R-Designer)
Gespeicherte Prozeduren und Funktionen können hinzugefügt werden die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] als <xref:System.Data.Linq.DataContext> Methoden. Aufrufen der Methode und übergeben der erforderlichen Parameter führt die gespeicherte Prozedur oder Funktion für die Datenbank und gibt die Daten im Rückgabetyp von den <xref:System.Data.Linq.DataContext> Methode. Ausführliche Informationen zu <xref:System.Data.Linq.DataContext> Methoden, finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
>  Mit gespeicherten Prozeduren kann auch das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Standardlaufzeitverhalten überschrieben werden, das beim Speichern von Änderungen von Entitätsklassen in einer Datenbank Einfüge-, Update- und Löschvorgänge durchführt. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Erstellen von DataContext-Methoden
 Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden durch Ziehen von gespeicherten Prozeduren oder Funktionen vom **Server-Explorer/Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

> [!NOTE]
>  Der Rückgabetyp einer generierten <xref:System.Data.Linq.DataContext>-Methode ist davon abhängig, wo Sie die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen. Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode mit dem Rückgabewert dieser Entitätsklasse erstellt. Wenn Sie Elemente in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch generierten Typ zurückgibt. Sie können ändern, den Rückgabetyp einer <xref:System.Data.Linq.DataContext> Methode nach dem Methodenbereich hinzugefügt. Um zu überprüfen oder ändern den Rückgabetyp eine <xref:System.Data.Linq.DataContext> -Methode, markieren Sie es, und Überprüfen der **Rückgabetyp** Eigenschaft in der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern Sie den Rückgabetyp einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>So erstellen Sie DataContext-Methoden, die automatisch generierte Typen zurückgeben

1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.

2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese auf einen leeren Bereich des [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     Die <xref:System.Data.Linq.DataContext> Methode wird mit einem automatisch generierten Rückgabetyp erstellt und wird in der **Methoden** Bereich.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>So erstellen Sie DataContext-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen

1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.

2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] auf eine vorhandene Entitätsklasse.

     Die <xref:System.Data.Linq.DataContext> Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und wird in der **Methoden** Bereich.

> [!NOTE]
>  Weitere Informationen zum Ändern des Rückgabetyp der vorhandenen <xref:System.Data.Linq.DataContext> Methoden, finden Sie unter [Vorgehensweise: Ändern Sie den Rückgabetyp einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Einführung in LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)