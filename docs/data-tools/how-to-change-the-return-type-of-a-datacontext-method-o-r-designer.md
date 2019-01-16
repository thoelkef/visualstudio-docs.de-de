---
title: 'Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 77d7b98367e343f90827429ad50be91527f7f303
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939436"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext> (erstellt basierend auf einer gespeicherten Prozedur oder Funktion) Methode hängt davon ab, in dem Sie die gespeicherte Prozedur oder Funktion im der **O/R Designer**. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einen leeren Bereich der Ablegen der **O/R Designer**, <xref:System.Data.Linq.DataContext> Methode, die einen automatisch generierten Typ zurückgibt, wird erstellt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie und klicken im Fenster **Eigenschaften** auf die Eigenschaft **Rückgabetyp**.

> [!NOTE]
>  <xref:System.Data.Linq.DataContext>-Methoden können nicht wiederhergestellt werden, wenn ein Rückgabetyp auf eine Entitätsklasse festgelegt ist, um so den automatisch generierten Typ mithilfe des Fensters **Eigenschaften** zurückzugeben. Zum Wiederherstellen einer <xref:System.Data.Linq.DataContext>-Methode zur Rückgabe eines automatisch generierten Typs müssen Sie das ursprüngliche Datenbankobjekt erneut auf den **O/R-Designer** ziehen.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse

1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.

2.  Wählen Sie im Fenster **Eigenschaften** die Option **Rückgabetyp** und anschließend in der Liste **Rückgabetyp** eine verfügbare Entitätsklasse aus. Wenn die gewünschte Entitätsklasse nicht in der Liste enthalten ist, hinzufügen oder erstellen sie im der **O/R Designer** um es der Liste hinzuzufügen.

3.  Speichern Sie die *DBML*-Datei.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ

1.  Wählen Sie im Bereich **Methoden** die <xref:System.Data.Linq.DataContext>-Methode aus, und löschen Sie sie.

2.  Ziehen Sie das Datenbankobjekt, das von **Server-Explorer** oder **Datenbank-Explorer** auf einen leeren Bereich, der die **O/R Designer**.

3.  Speichern Sie die *DBML*-Datei.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext methods (O/R Designer) (DataContext-Methoden (O/R-Designer))](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)