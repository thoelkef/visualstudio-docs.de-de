---
title: 'Gewusst wie: Ändern des Rückgabetyps einer DataContext-Methode (O / R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089356"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Gewusst wie: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext> (erstellt basierend auf einer gespeicherten Prozedur oder Funktion) Methode hängt davon ab, in dem Sie die gespeicherte Prozedur oder Funktion im der **O/R Designer**. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einen leeren Bereich der Ablegen der **O/R Designer**, <xref:System.Data.Linq.DataContext> Methode, die einen automatisch generierten Typ zurückgibt, wird erstellt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder Ändern des Rückgabetyps von einer <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und klicken Sie auf die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster.

> [!NOTE]
>  Sie können nicht rückgängig gemacht <xref:System.Data.Linq.DataContext> Methoden, die einen Rückgabetyp auf eine Entitätsklasse festgelegt, um den automatisch generierten Typ mit Zurückgeben der **Eigenschaften** Fenster. Wiederherstellen eine <xref:System.Data.Linq.DataContext> Methode, um einen automatisch generierten Typ zurückzugeben, müssen Sie das ursprüngliche Datenbankobjekt auf ziehen die **O/R-Designer** erneut.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse

1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.

2.  Wählen Sie **Rückgabetyp** in die **Eigenschaften** Fenster, und wählen Sie dann eine verfügbare Entitätsklasse-Klasse der **Rückgabetyp** Liste. Wenn die gewünschte Entitätsklasse nicht in der Liste enthalten ist, hinzufügen oder erstellen sie im der **O/R Designer** um es der Liste hinzuzufügen.

3.  Speichern Sie die *dbml* Datei.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ

1.  Wählen Sie die <xref:System.Data.Linq.DataContext> -Methode in der die **Methoden** Bereich und löschen Sie sie.

2.  Ziehen Sie das Datenbankobjekt, das von **Server-Explorer** oder **Datenbank-Explorer** auf einen leeren Bereich, der die **O/R Designer**.

3.  Speichern Sie die *dbml* Datei.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)