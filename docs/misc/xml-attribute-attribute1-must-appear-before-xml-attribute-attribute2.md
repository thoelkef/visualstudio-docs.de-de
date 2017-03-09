---
title: "XML-Attribut „attribute1“ muss vor dem XML-Attribut „attribute2“ angezeigt werden. | Microsoft Docs"
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
  - "bc31157"
  - "vbc31157"
helpviewer_keywords: 
  - "BC31157"
ms.assetid: d8d8769e-533d-454e-b145-99955ce45cc5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-Attribut „attribute1“ muss vor dem XML-Attribut „attribute2“ angezeigt werden.
Attribute in einem XML\-Dokumentliteral wurden in einer ungültigen Reihenfolge angegeben. Die gültige Attributreihenfolge für ein XML\-Dokumentliteral basiert auf der XML 1.0\-Spezifikation. Das `encoding`\-Attribut eines XML\-Dokumentliterals muss z. B. direkt auf das `version`\-Attribut folgen.  
  
 **Fehler\-ID:** BC31157  
  
### So beheben Sie diesen Fehler  
  
-   Aktualisieren Sie die Attributreihenfolge für das XML\-Dokumentliteral unter Anwendung der Richtlinien in der XML 1.0\-Spezifikation.  
  
## Siehe auch  
 [XML Literals and the XML 1.0 Specification](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification)   
 [XML Document Literal](/dotnet/visual-basic/language-reference/xml-literals/xml-document-literal)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)