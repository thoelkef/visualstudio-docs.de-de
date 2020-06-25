---
title: Speichern eines Datasets als XML
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8854581903ab58a327ff18be7b3b7c0f860a3b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281733"
---
# <a name="save-a-dataset-as-xml"></a>Speichern eines Datasets als XML

Greifen Sie auf die XML-Daten in einem DataSet zu, indem Sie die verfügbaren XML-Methoden für das DataSet aufrufen. Um die Daten im XML-Format zu speichern, können Sie entweder die- <xref:System.Data.DataSet.GetXml%2A> Methode oder die-Methode einer-Methode von aufzurufen <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet> .

Beim Aufrufen der- <xref:System.Data.DataSet.GetXml%2A> Methode wird eine Zeichenfolge zurückgegeben, die die Daten aus allen Datentabellen im DataSet enthält, die als XML formatiert sind.

Durch Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> -Methode werden die XML-formatierten Daten an eine von Ihnen angegebene Datei gesendet.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>So speichern Sie die Daten in einem DataSet als XML in einer Variablen

- Die <xref:System.Data.DataSet.GetXml%2A>-Methode gibt <xref:System.String> zurück. Deklarieren Sie eine Variable vom Typ, <xref:System.String> und weisen Sie Ihr die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode zu.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>So speichern Sie die Daten in einem DataSet als XML in einer Datei

- Die- <xref:System.Data.DataSet.WriteXml%2A> Methode verfügt über mehrere über Ladungen. Deklarieren Sie eine Variable, und weisen Sie Ihr einen gültigen Pfad zu, in dem die Datei gespeichert wird. Der folgende Code zeigt, wie die Daten in einer Datei gespeichert werden:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
