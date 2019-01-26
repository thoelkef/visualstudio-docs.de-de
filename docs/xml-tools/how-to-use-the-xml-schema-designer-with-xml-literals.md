---
title: 'Vorgehensweise: Verwenden des XML-Schema-Designers mit XML-Literalen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3883b4515ab304e2a247414f63c79db6314a654c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922077"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Vorgehensweise: Verwenden des XML-Schema-Designers mit XML-Literalen

In diesem Thema wird beschrieben, wie ein mit einem XML-Literal verknüpftes Schema in einem Visual Basic-Projekt angezeigt wird.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>So erstellen Sie ein neues Visual Basic-Konsolenanwendungsprojekt

1.  Starten Sie Visual Studio.

2.  Von der **Datei** , wählen Sie im Menü **neu**, und wählen Sie dann **Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt. Für **Projekttypen**Option **andere Sprachen** und wählen Sie dann **Visual Basic**. Für **Vorlagen**, wählen Sie die Konsolenanwendung. Geben Sie dann `XMLLiterals` in die **Namen** Feld und einen Projektspeicherort in das **Speicherort** Feld. Klicken Sie auf **OK**.

     Das neue Projekt wird erstellt. Das XMLLiterals-Projekt enthält eine Visual Basic-Quelldatei *"Module1.vb"*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>So fügen Sie dem Projekt eine vorhandene XSD-Datei hinzu

1.  Öffnen Sie eine neue Textdatei in Editor ein. Kopieren Sie die XML-schemabeispielcode aus [Bestellungsschema](../xml-tools/sample-xsd-file-simple-schema.md) und fügen Sie ihn in die Datei.

2.  Speichern Sie die Datei an einem Ort mit dem Namen *"purchaseorderschema.xsd"*.

3.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Namen des Projekts, wählen Sie **hinzufügen**, und wählen Sie dann **vorhandenes Element**. Die **vorhandenes Element** Dialogfeld wird angezeigt. Navigieren Sie zu der *"purchaseorderschema.xsd"* , wählen Sie ihn, und klicken Sie dann auf **hinzufügen**.

     Das Projekt XMLLiterals enthält nun zwei Dateien: *"Module1.vb"* und *"purchaseorderschema.xsd"*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>So fügen Sie basierend auf der XSD-Datei im Projekt Visual Basic-Code mit einem XML-Literal hinzu

1. Ersetzen Sie den Code in *"Module1.vb"* -Datei mit den folgenden Code:

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

2. Mit der rechten Maustaste in eines XML-Knotens in einem XML-Literal oder einem XML-Namespaceimport, und wählen Sie **im Schema-Explorer anzeigen**.

    Die **XML-Schema-Explorer** wird parallel zu Visual Basic-Datei, die mit dem XML-Schemaset verknüpfte XML-Literal angezeigt.