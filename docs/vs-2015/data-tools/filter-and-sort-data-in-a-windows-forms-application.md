---
title: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d1ea216e20045cd7b8cfba3c70a3126a673519be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175590"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtern und Sortieren von Daten in einer Windows Forms-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Daten können gefiltert werden, indem die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf einen Zeichenfolgenausdruck festlegt wird, der die gewünschten Datensätze zurückgibt.  
  
 Daten können sortiert werden, indem die <xref:System.Windows.Forms.BindingSource.Sort%2A>-Eigenschaft auf den Spaltennamen festgelegt wird, nach dem sortiert werden soll. Fügen Sie `DESC` an, um in absteigender Reihenfolge zu sortieren, oder fügen Sie `ASC` an, um in aufsteigender Reihenfolge zu sortieren.  
  
> [!NOTE]
>  Wenn Ihre Anwendung nicht verwendet <xref:System.Windows.Forms.BindingSource> -Komponenten, die Sie filtern und Sortieren von Daten mithilfe von <xref:System.Data.DataView> Objekte. Weitere Informationen finden Sie unter ["DataViews"](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Zum Filtern von Daten mithilfe einer BindingSource-Komponente  
  
-   Legen Sie die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf den zurückzugebenden Ausdruck fest. Im folgenden Code werden beispielsweise Kunden mit einem `CompanyName` zurückgegeben, der mit "B" beginnt:  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>So sortieren Sie Daten mithilfe einer BindingSource-Komponente  
  
-   Legen Sie die <xref:System.Windows.Forms.BindingSource.Sort%2A>-Eigenschaft auf die Spalte fest, nach der sortiert werden soll. Im folgenden Code werden beispielsweise Kunden in der Spalte `CompanyName` in absteigender Reihenfolge sortiert:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

