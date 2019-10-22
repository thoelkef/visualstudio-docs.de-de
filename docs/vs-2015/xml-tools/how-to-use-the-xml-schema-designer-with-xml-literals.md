---
title: 'Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656291"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie ein mit einem XML-Literal verknüpftes Schema in einem Visual Basic-Projekt angezeigt wird.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>So erstellen Sie ein neues Visual Basic-Konsolenanwendungsprojekt

1. Starten Sie Visual Studio 2010.

2. Wählen Sie im Menü **Datei** die Option **neu**aus, und wählen Sie dann **Projekt**aus. Das Dialogfeld **Neues Projekt** wird angezeigt. Wählen Sie für **Projekttypen**die Option **andere Sprachen aus,** und klicken Sie dann auf **Visual Basic**. Wählen Sie für **Vorlagen**die Option Konsolenanwendung aus. Geben Sie dann `XMLLiterals` in das Feld **Name** und einen Projekt Speicherort im Feld **Speicherort** ein. Klicken Sie auf **OK**.

     Das neue Projekt wird erstellt. Das Projekt "XMLLiterals" enthält eine Visual Basic-Quelldatei "Module1.vb".

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>So fügen Sie dem Projekt eine vorhandene XSD-Datei hinzu

1. Öffnen Sie im Editor eine neue Textdatei. Kopieren Sie den XML-Schema Beispielcode aus dem Bestell [Schema](../xml-tools/sample-xsd-file-simple-schema.md) , und fügen Sie ihn in die Datei ein.

2. Speichern Sie die Datei unter dem Namen "PurchaseOrderSchema.xsd" an einem beliebigen Speicherort.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamen, wählen Sie **Hinzufügen**aus, und wählen Sie dann **Vorhandenes Element...** aus. Das Dialogfeld **addebug-Element** wird angezeigt. Navigieren Sie zur Datei "PurchaseOrderSchema. xsd", wählen Sie Sie aus, und klicken Sie dann auf **Hinzufügen**.

     Das Projekt "XMLLiterals" enthält jetzt zwei Dateien: "Module1.vb" und "PurchaseOrderSchema.xsd".

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>So fügen Sie basierend auf der XSD-Datei im Projekt Visual Basic-Code mit einem XML-Literal hinzu

1. Ersetzen Sie den Code in der Datei "Module1.vb" durch folgenden Code:

    ```
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

     Der XML-Schema-Explorer wird neben einer Visual Basic-Datei angezeigt, die das mit dem XML-Schemaset verknüpfte XML-Literal enthält.
