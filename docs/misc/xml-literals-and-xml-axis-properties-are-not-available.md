---
title: "XML-Literale und XML-Achseneigenschaften sind nicht verf&#252;gbar | Microsoft Docs"
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
  - "bc31190"
  - "vbc31190"
helpviewer_keywords: 
  - "BC31190"
ms.assetid: cb861748-0ee4-40d3-a859-98ca6c39b4f4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-Literale und XML-Achseneigenschaften sind nicht verf&#252;gbar
XML\-Literale und XML\-Achseneigenschaften sind nicht verfügbar. Fügen Sie "System.Xml", "System.Xml.Linq" und "System.Core" Verweise hinzu.  
  
 Der kompilierte Code enthält XML\-Literale oder XML\-Achseneigenschaften, aber keinen Verweis auf die Assemblys, die zum Kompilieren von XML\-Literalen oder XML\-Achseneigenschaften erforderlich sind.  
  
 **Fehler\-ID:** BC31190  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie den Assemblys "System.Xml.dll", "System.Xml.Linq.dll" und "System.Core.dll" Verweise hinzu.  
  
## Siehe auch  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)