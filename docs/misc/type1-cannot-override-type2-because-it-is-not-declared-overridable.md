---
title: "&quot;&lt;Typ1&gt;&quot; kann &quot;&lt;Typ2&gt;&quot; nicht &#252;berschreiben, da er nicht als &quot;Overridable&quot; deklariert ist. | Microsoft Docs"
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
  - "bc31086"
  - "vbc31086"
helpviewer_keywords: 
  - "BC31086"
ms.assetid: ce071994-2e32-4460-a65d-f48f914386c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Typ1&gt;&quot; kann &quot;&lt;Typ2&gt;&quot; nicht &#252;berschreiben, da er nicht als &quot;Overridable&quot; deklariert ist.
Ein Member in einer abgeleiteten Klasse überschreibt einen Basisklassenmember, der nicht mit dem `Overridable`\-Modifizierer markiert ist.  
  
 **Fehler\-ID:** BC31086  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie dem überschriebenen Member in der Basisklasse den `Overridable`\-Modifizierer hinzu.  
  
2.  Verwenden Sie das `Shadows`\-Schlüsselwort, um das Element in der Basisklasse zu überschatten.  
  
## Siehe auch  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)