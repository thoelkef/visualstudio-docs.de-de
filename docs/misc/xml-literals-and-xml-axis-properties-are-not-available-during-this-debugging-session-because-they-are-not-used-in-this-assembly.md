---
title: "XML-Literale und XML-Achseneigenschaften sind in dieser Debugsitzung nicht verf&#252;gbar, da sie in dieser Assembly nicht verwendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31196"
  - "bc31196"
helpviewer_keywords: 
  - "BC31196"
ms.assetid: 36be5c92-dd6b-41d4-894a-2bd71d772092
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-Literale und XML-Achseneigenschaften sind in dieser Debugsitzung nicht verf&#252;gbar, da sie in dieser Assembly nicht verwendet werden
Im **Überwachungsfenster** oder im **Direktfenster** wurde während einer Debugsitzung, in der XML in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Features nicht verfügbar ist, auf ein XML\-Literal oder eine XML\-Achseneigenschaft verwiesen. Dies ist bei einer Assembly der Fall, die keinen XML\-Code in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Features verwendet oder bei der es sich um ein Releasebuild handelt.  
  
 **Fehler\-ID:** BC31196  
  
### So beheben Sie diesen Fehler  
  
-   Starten Sie eine neue Debugsitzung mithilfe des Debugbuilds der Assembly.  
  
## Siehe auch  
 [Debugging Your Visual Basic Application](/dotnet/visual-basic/developing-apps/debugging)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)