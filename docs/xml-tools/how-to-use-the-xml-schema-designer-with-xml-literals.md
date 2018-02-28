---
title: 'Vorgehensweise: Verwenden der XML-Schema-Designer mit XML-Literalen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: cda22612959e083cb1f0179d65554d38fab9cf03
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen
In diesem Thema wird beschrieben, wie ein mit einem XML-Literal verknüpftes Schema in einem Visual Basic-Projekt angezeigt wird.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>So erstellen Sie ein neues Visual Basic-Konsolenanwendungsprojekt  
  
1.  Starten Sie Visual Studio.  
  
2.  Aus der **Datei** klicken Sie im Menü **neu**, und wählen Sie dann **Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt. Für **-Projekttypen**Option **andere Sprachen** und wählen Sie dann **Visual Basic**. Für **Vorlagen**, wählen Sie die Konsolenanwendung. Geben Sie dann `XMLLiterals` in der **Namen** Feld und einen Projektspeicherort in das **Speicherort** Feld. Klicken Sie auf **OK**.  
  
     Das neue Projekt wird erstellt. Das Projekt "XMLLiterals" enthält eine Visual Basic-Quelldatei "Module1.vb".  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>So fügen Sie dem Projekt eine vorhandene XSD-Datei hinzu  
  
1.  Öffnen eine neue Textdatei in Notepad.Copy der XML-schemabeispielcode aus [Bestellungsschema](../xml-tools/sample-xsd-file-simple-schema.md) und fügen Sie ihn in der Datei.  
  
2.  Speichern Sie die Datei unter dem Namen "PurchaseOrderSchema.xsd" an einem beliebigen Speicherort.  
  
3.  Im Projektmappen-Explorer mit der Maustaste den Projektnamen, wählen Sie **hinzufügen**, und wählen Sie dann **vorhandenes Element...** . Die **AddExisting Element** Dialogfeld wird angezeigt. Navigieren Sie zu der Datei "purchaseorderschema.xsd", wählen Sie diese, und klicken Sie dann auf **hinzufügen**.  
  
     Das Projekt "XMLLiterals" enthält jetzt zwei Dateien: "Module1.vb" und "PurchaseOrderSchema.xsd".  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>So fügen Sie basierend auf der XSD-Datei im Projekt Visual Basic-Code mit einem XML-Literal hinzu  
  
1.  Ersetzen Sie den Code in der Datei "Module1.vb" durch folgenden Code:  
  
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
  
2.  Mit der rechten Maustaste in eines XML-Knotens in ein XML-Literal oder einem XML-Namespaceimport, und wählen Sie **im Schema-Explorer anzeigen**.  
  
     Der XML-Schema-Explorer wird neben einer Visual Basic-Datei angezeigt, die das mit dem XML-Schemaset verknüpfte XML-Literal enthält.