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
ms.workload:
- data-storage
ms.openlocfilehash: aaf566c211cd79657b67a5af72d53c718cd2507a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951458"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Deaktivieren von Einschränkungen beim Auffüllen von Datasets

Wenn Sie ein Dataset Einschränkungen (z. B. fremdschlüsseleinschränkungen) enthält, können sie Fehler im Zusammenhang Sequenznummern für das Dataset ausgeführten Vorgänge für das auslösen. Beispielsweise im Zusammenhang mit untergeordnete Datensätze vor dem Laden übergeordneten Datensätzen eine Einschränkung verletzt und einen Fehler verursachen können. Sobald Sie einen untergeordneten Datensatz laden, überprüft die Einschränkung das Vorhandensein des übergeordneten Datensatzes und löst einen Fehler aus.

Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden. Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>-Eigenschaft aufzuheben.

> [!NOTE]
> Validierungsereignisse (z. B. <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging>) wird nicht ausgelöst, wenn Einschränkungen deaktiviert sind.

## <a name="to-suspend-update-constraints-programmatically"></a>So heben Sie Aktualisierungseinschränkungen programmgesteuert auf

-   Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>So heben Sie Aktualisierungseinschränkungen mit dem Dataset-Designer auf

1.  Öffnen Sie das Dataset im DataSet-Designer **. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataSet.EnforceConstraints%2A> auf `false`fest.

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)