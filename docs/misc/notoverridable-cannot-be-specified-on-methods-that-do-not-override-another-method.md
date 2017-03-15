---
title: "&quot;NotOverridable&quot; kann nicht f&#252;r Methoden angegeben werden, die keine andere Methode &#252;berschreiben. | Microsoft Docs"
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
  - "vbc31088"
  - "bc31088"
helpviewer_keywords: 
  - "BC31088"
ms.assetid: 0241197c-51fa-48b8-9a2a-4205d25641d3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;NotOverridable&quot; kann nicht f&#252;r Methoden angegeben werden, die keine andere Methode &#252;berschreiben.
Eigenschaften und Methoden sind standardmäßig `NotOverridable`. Der `NotOverridable`\-Modifizierer kann nur für Methoden verwendet werden, die eine andere Eigenschaft oder Methode überschreiben.  
  
 **Fehler\-ID:** BC31088  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den `NotOverridable`\-Modifizierer aus den Eigenschaften und Methoden, die keinen anderen Member überschreiben.  
  
## Siehe auch  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)