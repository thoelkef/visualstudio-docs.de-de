---
title: "&#39;Sub&#39; oder &#39;Function&#39; nach &#39;Delegate&#39; erwartet. | Microsoft Docs"
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
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub&#39; oder &#39;Function&#39; nach &#39;Delegate&#39; erwartet.
Von einer `Delegate`\-Anweisung wird keine `Sub`\- oder `Function`\-Prozedur angegeben. Das `Sub`\- oder `Function`\-Schlüsselwort muss direkt auf das `Delegate`\-Schlüsselwort folgen.  
  
 **Fehler\-ID:** BC30278  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie das `Sub`\- oder `Function`\-Schlüsselwort direkt hinter `Delegate` hinzu.  
  
2.  Geben Sie entsprechend einen Prozedurnamen, eine Argumentliste und einen Rückgabetyp an.  
  
## Siehe auch  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)