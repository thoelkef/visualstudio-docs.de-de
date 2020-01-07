---
title: 'Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b4001e705cc69e07242abeeef5919573b264c5e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592658"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen

In diesem Thema wird beschrieben, wie ein mit einem XML-Literal verknüpftes Schema in einem Visual Basic-Projekt angezeigt wird.

## <a name="create-a-new-visual-basic-project"></a>Erstellen eines neuen Visual Basic Projekts

1. Öffnen Sie Visual Studio.

2. Erstellen Sie ein neues Visual Basic **Konsolen-App** -Projekt mit dem Namen **XMLLiterals**.

     Das neue Projekt enthält eine Visual Basic Quelldatei, *Module1. vb*.

## <a name="add-an-existing-xsd-file"></a>Vorhandene XSD-Datei hinzufügen

1. Öffnen Sie im Editor eine neue Textdatei. Kopieren Sie den XML-Schema Beispielcode aus dem Bestell [Schema](../xml-tools/sample-xsd-file-simple-schema.md) , und fügen Sie ihn in die Datei ein.

2. Speichern Sie die Datei an einem Speicherort mit dem Namen " *PurchaseOrderSchema. xsd*".

3. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, wählen Sie **Hinzufügen**aus, und wählen Sie dann **Vorhandenes Element**aus. Das Dialogfeld **addebug-Element** wird angezeigt. Navigieren Sie zur Datei " *PurchaseOrderSchema. xsd* ", wählen Sie Sie aus, und klicken Sie dann auf **Hinzufügen**.

     Das Projekt "XMLLiterals" enthält jetzt zwei Dateien: *Module1. vb* und *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Code hinzufügen

So fügen Sie Visual Basic Code mithilfe eines XML-Literals hinzu, basierend auf der im Projekt enthaltenen XSD-Datei:

1. Ersetzen Sie den Code in der Datei *Module1. vb* durch den folgenden Code:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Klicken Sie mit der rechten Maustaste auf einen beliebigen XML-Knoten in einem XML-Literaltyp oder auf einen XML-Namespace Import, und wählen Sie **im**

   Der **XML-Schema-Explorer** wird nebeneinander mit einer Visual Basic-Datei angezeigt, die dem XML-Schema Satz das XML-Literalzeichen zugeordnet ist.
