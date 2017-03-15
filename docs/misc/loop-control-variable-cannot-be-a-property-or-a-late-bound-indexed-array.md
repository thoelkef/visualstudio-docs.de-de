---
title: "Eine Schleifensteuerungsvariable kann keine Eigenschaft und kein sp&#228;t gebundenes indiziertes Array sein. | Microsoft Docs"
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
  - "bc30039"
  - "vbc30039"
helpviewer_keywords: 
  - "BC30039"
ms.assetid: 63846449-b1df-4626-bf99-36fa9b187799
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Schleifensteuerungsvariable kann keine Eigenschaft und kein sp&#228;t gebundenes indiziertes Array sein.
Die Variable, die zum Durchlaufen einer `For`\-Schleife verwendet wird, muss einen numerischen Datentyp aufweisen.  
  
 **Fehler\-ID:** BC30039  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Deklaration der Schleifensteuerungsvariablen, um `Integer`, `Short`, `Long`, `Byte`, `Single`, `Double` oder `Decimal` anzugeben.  
  
## Siehe auch  
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)