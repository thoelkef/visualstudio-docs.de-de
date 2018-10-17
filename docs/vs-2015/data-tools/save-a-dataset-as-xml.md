---
title: Speichern eines Datasets als XML | Microsoft-Dokumentation
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a91bc594f2f028f7dfc7a11263b7aac23150b7f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287572"
---
# <a name="save-a-dataset-as-xml"></a>Speichern eines Datasets als XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die XML-Daten in einem Dataset können durch Aufrufen der verfügbaren XML-Methoden für das Dataset zugegriffen werden. Um die Daten im XML-Format zu speichern, können Sie rufen Sie entweder die <xref:System.Data.DataSet.GetXml%2A> Methode oder der <xref:System.Data.DataSet.WriteXml%2A> Methode eine <xref:System.Data.DataSet>.  
  
 Aufrufen der <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine Zeichenfolge, die die Daten aus allen Datentabellen im Dataset enthält, die als XML formatiert sind.  
  
 Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> Methode sendet die XML-formatierte Daten in eine Datei, die Sie angeben.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Um die Daten in einem Dataset als XML einer Variablen speichern  
  
-   Die <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine <xref:System.String>. Dies bedeutet, dass Sie eine Variable vom Typ deklarieren <xref:System.String> und weisen sie die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Um die Daten in einem Dataset in eine Datei im XML-Format zu speichern  
  
-   Die <xref:System.Data.DataSet.WriteXml%2A> -Methode weist mehrere Überladungen. Der folgende Code zeigt, wie Sie die Daten in eine Datei zu speichern. Deklarieren Sie eine Variable, und weisen sie einen gültigen Pfad für die Datei zu speichern.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

