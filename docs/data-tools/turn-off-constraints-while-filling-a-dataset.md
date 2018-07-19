---
title: Deaktivieren von Einschränkungen beim Auffüllen von Datasets
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d128216f84228c9cd4946f9a38c6c1b7845f92f1
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117237"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Deaktivieren von Einschränkungen beim Auffüllen von Datasets

Wenn Sie ein Dataset Einschränkungen (z. B. fremdschlüsseleinschränkungen) enthält, können sie Fehler im Zusammenhang Sequenznummern für das Dataset ausgeführten Vorgänge für das auslösen. Beispielsweise im Zusammenhang mit untergeordnete Datensätze vor dem Laden übergeordneten Datensätzen eine Einschränkung verletzt und einen Fehler verursachen können. Sobald Sie einen untergeordneten Datensatz laden, wird die Einschränkung für den zugehörigen übergeordneten Datensatz überprüft und ein Fehler ausgelöst.

Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden. Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>-Eigenschaft aufzuheben.

> [!NOTE]
> Validierungsereignisse (z. B. <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging>) wird nicht ausgelöst, wenn Einschränkungen deaktiviert sind.

## <a name="to-suspend-update-constraints-programmatically"></a>So heben Sie Aktualisierungseinschränkungen programmgesteuert auf

-   Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>So heben Sie Aktualisierungseinschränkungen mit dem Dataset-Designer auf

1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  In der **Eigenschaften** legen die <xref:System.Data.DataSet.EnforceConstraints%2A> Eigenschaft `false`.

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)