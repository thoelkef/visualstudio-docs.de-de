---
title: 'Vorgehensweise: Ändern des Rückgabe Typs einer DataContext-Methode (O-R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658841"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode, die basierend auf einer gespeicherten Prozedur oder Funktion erstellt wurde, unterscheidet sich abhängig von dem Ort, an dem die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] abgelegt wurde. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie und klicken im Fenster **Eigenschaften** auf die Eigenschaft **Rückgabetyp**.

> [!NOTE]
> <xref:System.Data.Linq.DataContext>-Methoden können nicht wiederhergestellt werden, wenn ein Rückgabetyp auf eine Entitätsklasse festgelegt ist, um so den automatisch generierten Typ mithilfe des Fensters **Eigenschaften** zurückzugeben. Zum Wiederherstellen einer <xref:System.Data.Linq.DataContext>-Methode zur Rückgabe eines automatisch generierten Typs müssen Sie das ursprüngliche Datenbankobjekt erneut auf den O/R-Designer ziehen.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse

1. Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.

2. Wählen Sie im Fenster **Eigenschaften** die Option **Rückgabetyp** und anschließend in der Liste **Rückgabetyp** eine verfügbare Entitätsklasse aus. Wenn die gewünschte Entitäts Klasse nicht in der Liste enthalten ist, fügen Sie Sie hinzu, oder erstellen Sie Sie in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], um Sie der Liste hinzuzufügen.

3. Speichern Sie die DBML-Datei.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ

1. Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus, und löschen Sie sie.

2. Ziehen Sie das Datenbankobjekt aus **Server-Explorer** /**Datenbank-Explorer** auf einen leeren Bereich des O/R-Designers.

3. Speichern Sie die DBML-Datei.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (o/r-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
