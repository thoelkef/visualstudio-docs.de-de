---
title: Zuordnen von DataContext-Methoden zu Sprocs und Functions
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 21ea455e6cc29d17f9050e54dd2f8d11033320ac
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742907"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)

Sie können dem **O/R-Designer** gespeicherte Prozeduren und Funktionen als Methoden hinzufügen <xref:System.Data.Linq.DataContext> . Durch Aufrufen der Methode und Übergeben der erforderlichen Parameter wird die gespeicherte Prozedur oder Funktion in der Datenbank ausgeführt und gibt die Daten im Rückgabetyp der <xref:System.Data.Linq.DataContext>-Methode zurück. Ausführliche Informationen zu- <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Sie können auch gespeicherte Prozeduren verwenden, um das standardmäßige Laufzeitverhalten zu überschreiben, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] das Einfügungen, Updates und Löschungen durchführt, wenn Änderungen aus Entitäts Klassen in einer Datenbank gespeichert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Erstellen von DataContext-Methoden

Sie können Methoden erstellen, <xref:System.Data.Linq.DataContext> indem Sie gespeicherte Prozeduren oder Funktionen von <strong>Server-Explorer oder * * Datenbank-Explorer</strong> auf den **O/R-Designer**ziehen.

> [!NOTE]
> Der Rückgabetyp der generierten Methode unterscheidet sich abhängig davon, <xref:System.Data.Linq.DataContext> wo Sie die gespeicherte Prozedur oder Funktion im **O/R-Designer**ablegen. Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode mit dem Rückgabetyp dieser Entitätsklasse erstellt. Wenn Sie Elemente in einem leeren Bereich des **O/R-Designers** ablegen <xref:System.Data.Linq.DataContext> , wird eine Methode erstellt, die einen automatisch generierten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, nachdem Sie diese dem Bereich **Methoden** hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Rückgabe Typs einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>So erstellen Sie DataContext-Methoden, die automatisch generierte Typen zurückgeben

1. Erweitern Sie in **Server-Explorer** oder **Datenbank-Explorer**den Knoten **gespeicherte Prozeduren** der Datenbank, mit der Sie arbeiten.

2. Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie Sie auf einen leeren Bereich des **O/R-Designers**.

     Die <xref:System.Data.Linq.DataContext>-Methode wird mit einem automatisch generierten Rückgabetyp erstellt und im Bereich **Methoden** angezeigt.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>So erstellen Sie DataContext-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen

1. Erweitern Sie in **Server-Explorer** oder **Datenbank-Explorer**den Knoten **gespeicherte Prozeduren** der Datenbank, mit der Sie arbeiten.

2. Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie Sie in den **O/R-Designer**auf eine vorhandene Entitäts Klasse.

     Die <xref:System.Data.Linq.DataContext>-Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und im Bereich **Methoden** angezeigt.

> [!NOTE]
> Weitere Informationen zum Ändern des Rückgabe Typs vorhandener <xref:System.Data.Linq.DataContext> Methoden finden Sie unter Gewusst [wie: Ändern des Rückgabe Typs einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Einführung in LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)
