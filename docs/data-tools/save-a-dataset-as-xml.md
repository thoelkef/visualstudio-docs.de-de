---
title: Speichern Sie ein Dataset als XML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9d91e964ddade89c8bce8f0519517995b7d75a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="save-a-dataset-as-xml"></a>Speichern Sie ein Dataset als XML
Die XML-Daten in einem Dataset können durch Aufrufen der verfügbaren XML-Methoden für das Dataset zugegriffen werden. Um die Daten im XML-Format zu speichern, rufen Sie entweder die <xref:System.Data.DataSet.GetXml%2A> Methode oder die <xref:System.Data.DataSet.WriteXml%2A> Methode von einer <xref:System.Data.DataSet>.  
  
 Aufrufen der <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine Zeichenfolge, die die Daten aus allen Datentabellen im Dataset enthält, die als XML formatiert sind.  
  
 Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> Methode sendet die XML-formatierte Daten in eine Datei, die Sie angeben.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Um die Daten in einem Dataset als XML in einer Variablen zu speichern  
  
-   Die <xref:System.Data.DataSet.GetXml%2A> Methode gibt ein <xref:System.String>. Dies bedeutet, dass Sie eine Variable des Typs deklarieren <xref:System.String> und weisen sie die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Um die Daten in einem Dataset als XML in einer Datei speichern  
  
-   Die <xref:System.Data.DataSet.WriteXml%2A> -Methode weist mehrere Überladungen. Der folgende Code zeigt, wie die Daten in eine Datei zu speichern. Deklarieren Sie eine Variable aus, und weisen sie einen gültigen Pfad für die Datei zu speichern.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)