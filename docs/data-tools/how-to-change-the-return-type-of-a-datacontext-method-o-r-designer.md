---
title: 'Vorgehensweise: Ändern Sie den Rückgabetyp einer DataContext-Methode (O-R-Designer)'
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
ms.openlocfilehash: f4f1c9ffe0b9e6e7a112b50325e53955e5a97f01
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921868"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Vorgehensweise: Ändern Sie den Rückgabetyp einer DataContext-Methode (O/R-Designer)
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode, die basierend auf einer gespeicherten Prozedur oder Funktion erstellt wurde, unterscheidet sich abhängig von dem Ort, an dem die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] abgelegt wurde. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder ändern den Rückgabetyp der eine <xref:System.Data.Linq.DataContext> Methode auszuwählen, und klicken Sie auf die **Rückgabetyp** Eigenschaft in der **Eigenschaften** Fenster.

> [!NOTE]
>  Es können keine zurückgesetzt <xref:System.Data.Linq.DataContext> Methoden, die einen Rückgabetyp auf eine Entitätsklasse festgelegt, um mit automatisch generierten Typ zurückgeben müssen die **Eigenschaften** Fenster. Zum Wiederherstellen einer <xref:System.Data.Linq.DataContext>-Methode zur Rückgabe eines automatisch generierten Typs müssen Sie das ursprüngliche Datenbankobjekt erneut auf den O/R-Designer ziehen.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse

1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.

2.  Wählen Sie **Rückgabetyp** in der **Eigenschaften** Fenster und wählen Sie dann eine verfügbare Entitätsklasse Klasse, der **Rückgabetyp** Liste. Wenn die gewünschte Entitätsklasse nicht in der Liste enthalten ist, hinzufügen zu oder erstellen Sie ihn in die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] um es der Liste hinzuzufügen.

3.  Speichern Sie die DBML-Datei.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ

1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus, und löschen Sie sie.

2.  Ziehen Sie das Datenbankobjekt von **Server-Explorer**/**Datenbank-Explorer** auf einen leeren Bereich des O/R-Designers.

3.  Speichern Sie die DBML-Datei.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden zugeordnet werden, um gespeicherte Prozeduren und Funktionen (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)