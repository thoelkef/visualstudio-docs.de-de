---
title: Deaktivieren von Einschränkungen beim Auffüllen von Datasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c47d3cb5e02117cb75ab86579b0cb3b166bd510
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259908"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Deaktivieren von Einschränkungen beim Auffüllen von Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Wenn Sie ein Dataset Einschränkungen (z. B. fremdschlüsseleinschränkungen) enthält, lösen Fehler aus Sequenznummern für das Dataset ausgeführten Vorgänge im Zusammenhang. Z. B. kann untergeordnete Datensätze vor dem Loadingrelated übergeordneten Datensätze gegen eine Einschränkung verstoßen und einen Fehler verursachen. Sobald Sie einen untergeordneten Datensatz laden, wird die Einschränkung für den zugehörigen übergeordneten Datensatz überprüft und ein Fehler ausgelöst.  
  
 Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden. Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>-Eigenschaft aufzuheben.  
  
> [!NOTE]
>  Validierungsereignisse (z. B. <xref:System.Data.DataTable.ColumnChanging> und<xref:System.Data.DataTable.RowChanging>) wird nicht ausgelöst, wenn Einschränkungen deaktiviert sind.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>So heben Sie Aktualisierungseinschränkungen programmgesteuert auf  
  
-   Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>So heben Sie Aktualisierungseinschränkungen mit dem Dataset-Designer auf  
  
1.  Öffnen Sie das Dataset in den [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md). Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataSet.EnforceConstraints%2A> auf `false`fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)

