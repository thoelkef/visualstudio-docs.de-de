---
title: "Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Verwenden des XML-Schema-Designers mit XML-Literalen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie ein mit einem XML\-Literal verknüpftes Schema in einem Visual Basic\-Projekt angezeigt wird.  
  
### So erstellen Sie ein neues Visual Basic\-Konsolenanwendungsprojekt  
  
1.  Starten Sie Visual Studio 2010.  
  
2.  Klicken Sie im Menü **Datei** auf **Neu**, und wählen Sie anschließend **Projekt** aus.Das Dialogfeld **Neues Projekt** wird angezeigt.Wählen Sie für **Projekttypen** die Option **Andere Sprachen** aus, und klicken Sie dann auf **Visual Basic**.Wählen Sie für **Vorlagen** die Option "Konsolenanwendung" aus.Geben Sie dann `XMLLiterals` in das Feld **Name** und einen Projektspeicherort in das Feld **Speicherort** ein.Klicken Sie auf **OK**.  
  
     Das neue Projekt wird erstellt.Das Projekt "XMLLiterals" enthält eine Visual Basic\-Quelldatei "Module1.vb".  
  
### So fügen Sie dem Projekt eine vorhandene XSD\-Datei hinzu  
  
1.  Öffnen Sie im Editor eine neue Textdatei.Kopieren Sie den XML\-Schemabeispielcode aus [Bestellungsschema](../xml-tools/sample-xsd-file-simple-schema.md), und fügen Sie ihn in die Datei ein.  
  
2.  Speichern Sie die Datei unter dem Namen "PurchaseOrderSchema.xsd" an einem beliebigen Speicherort.  
  
3.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf den Projektnamen, wählen Sie **Hinzufügen** aus, und klicken Sie dann auf **Vorhandenes Element**.Das Dialogfeld **VorhandenesElement hinzufügen** wird angezeigt.Navigieren Sie zur Datei "PurchaseOrderSchema.xsd", wählen Sie die Datei aus, und klicken Sie dann auf **Hinzufügen**.  
  
     Das Projekt "XMLLiterals" enthält jetzt zwei Dateien: "Module1.vb" und "PurchaseOrderSchema.xsd".  
  
### So fügen Sie basierend auf der XSD\-Datei im Projekt Visual Basic\-Code mit einem XML\-Literal hinzu  
  
1.  Ersetzen Sie den Code in der Datei "Module1.vb" durch folgenden Code:  
  
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
  
2.  Klicken Sie mit der rechten Maustaste auf einen XML\-Knoten in einem XML\-Literal oder einem XML\-Namespaceimport, und wählen Sie **In XML\-Schema\-Explorer anzeigen** aus.  
  
     Der XML\-Schema\-Explorer wird neben einer Visual Basic\-Datei angezeigt, die das mit dem XML\-Schemaset verknüpfte XML\-Literal enthält.