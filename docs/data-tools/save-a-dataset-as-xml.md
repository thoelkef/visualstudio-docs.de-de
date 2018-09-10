---
title: Speichern eines Datasets als XML
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a1b0c453f3b48b12c5a77fce86789a66fe77c26
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173996"
---
# <a name="save-a-dataset-as-xml"></a>Speichern eines Datasets als XML

Greifen Sie die XML-Daten in einem Dataset wird durch Aufrufen von verfügbaren XML-Methoden für das Dataset zu. Um die Daten im XML-Format zu speichern, können Sie rufen Sie entweder die <xref:System.Data.DataSet.GetXml%2A> Methode oder der <xref:System.Data.DataSet.WriteXml%2A> Methode eine <xref:System.Data.DataSet>.

Aufrufen der <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine Zeichenfolge, die die Daten aus allen Datentabellen im Dataset enthält, die als XML formatiert sind.

Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> Methode sendet die XML-formatierte Daten in eine Datei, die Sie angeben.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Um die Daten in einem Dataset als XML einer Variablen speichern

- Die <xref:System.Data.DataSet.GetXml%2A> Methode gibt eine <xref:System.String>. Deklarieren Sie eine Variable vom Typ <xref:System.String> und weisen sie die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Um die Daten in einem Dataset in eine Datei im XML-Format zu speichern

- Die <xref:System.Data.DataSet.WriteXml%2A> -Methode weist mehrere Überladungen. Deklarieren Sie eine Variable, und weisen sie einen gültigen Pfad für die Datei zu speichern. Der folgende Code zeigt, wie Sie die Daten in einer Datei speichern:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)