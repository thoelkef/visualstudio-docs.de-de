---
title: 'Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O / R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ae5fb4b3785bde0e092f68b62a9b030069a52aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942698"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)

Sie können gespeicherte Prozeduren und Funktionen zum Hinzufügen der **O/R Designer** als <xref:System.Data.Linq.DataContext> Methoden. Aufrufen der Methode und die erforderlichen Parameter übergeben, führt die gespeicherte Prozedur oder Funktion für die Datenbank, und gibt die Daten in den Rückgabetyp der <xref:System.Data.Linq.DataContext> Methode. Ausführliche Informationen zu <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Sie können auch gespeicherte Prozeduren verwenden, um die Standardeinstellung überschreiben [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Laufzeitverhalten führen konnte, die Einfüge-, Update- und Löschvorgänge ausführt, wenn Änderungen von Entitätsklassen in einer Datenbank gespeichert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Erstellen Sie DataContext-Methoden

Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden durch Ziehen von gespeicherten Prozeduren oder Funktionen aus <strong>Server-Explorer oder ** Datenbank-Explorer</strong> auf die **O/R-Designer**.

> [!NOTE]
> Der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode hängt davon ab, in dem Sie die gespeicherte Prozedur oder Funktion das **O/R Designer**. Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode mit dem Rückgabewert dieser Entitätsklasse erstellt. Elemente auf einen leeren Bereich der Ablegen der **O/R Designer** erstellt eine <xref:System.Data.Linq.DataContext> Methode, die einen automatisch generierten Typ zurückgibt. Sie können den Rückgabetyp ändern eine <xref:System.Data.Linq.DataContext> Methode nach dem Hinzufügen zu den **Methoden** Bereich. Um zu überprüfen oder Ändern des Rückgabetyps des eine <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und überprüfen Sie die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>So erstellen Sie DataContext-Methoden, die automatisch generierte Typen zurückgeben

1.  In **Server-Explorer** oder **Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank, mit denen Sie arbeiten.

2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie es in einen leeren Bereich der **O/R Designer**.

     Die <xref:System.Data.Linq.DataContext> Methode wird mit einem automatisch generierten Rückgabetyp erstellt und wird in der **Methoden** Bereich.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>So erstellen Sie DataContext-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen

1.  In **Server-Explorer** oder **Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank, mit denen Sie arbeiten.

2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie es in einer existierenden Entitätsklasse in der **O/R Designer**.

     Die <xref:System.Data.Linq.DataContext> Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und wird in der **Methoden** Bereich.

> [!NOTE]
> Informationen zum Ändern des Rückgabetyps vorhandener <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Einführung in LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)