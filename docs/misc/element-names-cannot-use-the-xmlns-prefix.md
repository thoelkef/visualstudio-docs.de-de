---
title: "In Elementnamen darf das Pr&#228;fix &quot;xmlns&quot; nicht verwendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31189"
  - "bc31189"
helpviewer_keywords: 
  - "BC31189"
ms.assetid: 88716bb5-6766-4180-b2ed-1d1bee0ff7a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In Elementnamen darf das Pr&#228;fix &quot;xmlns&quot; nicht verwendet werden.
Ein XML\-Elementliteral wurde mit dem XML\-Namespacepräfix `xmlns` angegeben. Zum Beispiel:  
  
```vb#  
Dim elem = <xmlns:ElementName>  
```  
  
 Die XML 1.0\-Spezifikation gibt `xmlns` als ein reserviertes Wort an.  
  
 **Fehler\-ID:** BC31189  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie das XML\-Namespacepräfix in einen gültigen Wert, oder entfernen Sie das Präfix.  
  
## Siehe auch  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)