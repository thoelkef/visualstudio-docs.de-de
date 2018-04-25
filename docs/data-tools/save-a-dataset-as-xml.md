---
title: Speichern Sie ein Dataset als XML
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
ms.openlocfilehash: b384c7d2042611be84322fd5a842f1ba5ca8de9c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="save-a-dataset-as-xml"></a>Speichern Sie ein Dataset als XML

Die XML-Daten in einem Dataset können durch Aufrufen der verfügbaren XML-Methoden für das Dataset zugegriffen werden. Um die Daten im XML-Format zu speichern, rufen Sie entweder die <xref:System.Data.DataSet.GetXml%2A> Methode oder die <xref:System.Data.DataSet.WriteXml%2A> Methode von einer <xref:System.Data.DataSet>.

Aufrufen der <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine Zeichenfolge, die die Daten aus allen Datentabellen im Dataset enthält, die als XML formatiert sind.

Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> Methode sendet die XML-formatierte Daten in eine Datei, die Sie angeben.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Um die Daten in einem Dataset als XML in einer Variablen zu speichern

- Die <xref:System.Data.DataSet.GetXml%2A> Methode gibt ein <xref:System.String>. Deklarieren Sie eine Variable vom Typ <xref:System.String> und weisen sie die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Um die Daten in einem Dataset als XML in einer Datei speichern

- Die <xref:System.Data.DataSet.WriteXml%2A> -Methode weist mehrere Überladungen. Deklarieren Sie eine Variable aus, und weisen sie einen gültigen Pfad für die Datei zu speichern. Der folgende Code zeigt, wie die Daten in eine Datei zu speichern:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)