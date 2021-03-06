---
title: Deaktivieren von Einschränkungen beim Auffüllen eines Datasets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667166"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Deaktivieren von Einschränkungen beim Auffüllen von Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn ein DataSet Einschränkungen (z. b. Foreign Key-Einschränkungen) enthält, kann der Fehler im Zusammenhang mit der Reihenfolge der Vorgänge, die für das DataSet ausgeführt werden, entstehen. Beispielsweise kann das Laden von untergeordneten Datensätzen vor übergeordneten Datensätzen mit loadingrelated gegen eine Einschränkung verstoßen und einen Fehler verursachen. Sobald Sie einen untergeordneten Datensatz laden, überprüft die Einschränkung das Vorhandensein des übergeordneten Datensatzes und löst einen Fehler aus.

 Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden. Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>-Eigenschaft aufzuheben.

> [!NOTE]
> Validierungs Ereignisse (z. b. <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> ) werden nicht ausgelöst, wenn Einschränkungen deaktiviert werden.

### <a name="to-suspend-update-constraints-programmatically"></a>So heben Sie Aktualisierungseinschränkungen programmgesteuert auf

- Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>So heben Sie Aktualisierungseinschränkungen mit dem Dataset-Designer auf

1. Öffnen Sie das Dataset im DataSet-Designer. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Datasets in der DataSet-Designer](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataSet.EnforceConstraints%2A> auf `false`fest.

## <a name="see-also"></a>Weitere Informationen
 [Auffüllen von Datasets mithilfe von TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) - [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)
