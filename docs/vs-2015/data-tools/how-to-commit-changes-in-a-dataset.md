---
title: 'Vorgehensweise: Änderungen in einem Dataset | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 41d27c248763f42db6543db0a9b4e56e4c4eac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276431"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Gewusst wie: Ausführen eines Commit für Änderungen in einem Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Änderungen an Datensätzen in einem Dataset aktualisieren, einfügen und Löschen von Datensätzen vornehmen, verwaltet das Dataset ursprüngliche und aktuelle Versionen der einzelnen Datensätze. Außerdem wird jede Zeile des <xref:System.Data.DataRow.RowState%2A> Eigenschaft behält den Überblick, ob die Datensätze in den ursprünglichen Zustand sind haben wurde aktualisiert, eingefügt oder gelöscht. Diese Informationen sind hilfreich, wenn Sie eine bestimmte Version einer Zeile suchen müssen. In der Regel erhalten Sie eine Teilmenge aller geänderten Datensätze zu einem anderen Prozess zu senden. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von geänderten Zeilen](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Nachdem Sie alle geänderten Zeilen verarbeitet, Sie können die Änderungen durch Aufrufen der `AcceptChanges` Methode der <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow>. Die `AcceptChanges` Methode automatisch aufgerufen, wenn der Aufruf der updatemethoden von einer [TableAdapter](../data-tools/tableadapter-overview.md) oder Datenadapters. Rufen Sie `AcceptChanges` nach der Übermittlung von Änderungen an einer Datenbank.  
  
 Beim Aufruf <xref:System.Data.DataSet.AcceptChanges%2A> auf die <xref:System.Data.DataSet>, <xref:System.Data.DataRow> Objekte immer noch im Bearbeitungsmodus erfolgreich zu beenden, ihre Änderungen. Die <xref:System.Data.DataRow.RowState%2A> Eigenschaft der einzelnen <xref:System.Data.DataRow> ändert sich ebenfalls; <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState> Zeilen werden <xref:System.Data.DataRowState>, und <xref:System.Data.DataRowState> Zeilen entfernt werden.  
  
 Wenn die <xref:System.Data.DataSet> enthält <xref:System.Data.ForeignKeyConstraint> Objekte Aufrufen der <xref:System.Data.DataSet.AcceptChanges%2A> Methode bewirkt auch, dass die <xref:System.Data.AcceptRejectRule> erzwungen werden.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Übergeben von Änderungen in einem dataset  
  
-   Rufen Sie die `AcceptChanges` -Methode an eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow> um die Änderungen in diesen Objekten zu übernehmen.  
  
     Das folgende Beispiel zeigt das Aufrufen der `AcceptChanges` Methode, um die Änderungen in der `Customers` Tabelle nach der Aktualisierung einer Datenquelle:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Vorgehensweise: Abrufen von geänderten Zeilen](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)