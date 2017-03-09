---
title: "XML-Nachfolgerelemente k&#246;nnen nicht vom Typ &quot;Typ&quot; ausgew&#228;hlt werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-Nachfolgerelemente k&#246;nnen nicht vom Typ &quot;Typ&quot; ausgew&#228;hlt werden.
Mit einem XML\-Nachfolgerelement wurde auf ein Objekt verwiesen, das nicht vom Typ <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> oder `IEnumerable(Of XElement)` ist. Weitere Informationen finden Sie unter [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **Fehler\-ID:** BC36809  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass das Objekt, von dem Sie auf ein Nachfolgerelement verweisen, als <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> oder `IEnumerable(Of XElement)` stark typisiert ist. Beachten Sie folgendes Beispiel:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## Siehe auch  
 [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)