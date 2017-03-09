---
title: "Zeichen mit voller Breite k&#246;nnen nicht als XML-Trennzeichen verwendet werden. | Microsoft Docs"
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
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Zeichen mit voller Breite k&#246;nnen nicht als XML-Trennzeichen verwendet werden.
Es wurde ein XML\-Literal definiert, das ein Zeichen mit voller Breite als Trennzeichen enthält. Zeichen mit voller Breite werden auch als Breitzeichen oder Multibytezeichen bezeichnet.  
  
 **Fehler\-ID:** BC31197  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Zeichen mit voller Breite aus der XML\-Literaldefinition, und ersetzen Sie es durch ein gültiges ANSI\-Trennzeichen. Folgende Zeichen gehören zu den gültigen Trennzeichen: `<`, `>`, `=`, `:`, `/`.  
  
## Siehe auch  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Zeichencodierung in .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)