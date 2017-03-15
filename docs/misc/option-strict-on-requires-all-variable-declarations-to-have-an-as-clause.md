---
title: "&quot;Option Strict On&quot; erfordert von allen Variablendeklarationen eine As-Klausel. | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; erfordert von allen Variablendeklarationen eine As-Klausel.
Eine Deklaration enthält eine deklarierte Variable ohne `As`\-Klausel. Wenn `Option Strict` \= `On` ist, muss jede Variable, jede Eigenschaft, jedes Prozedurargument und jede Funktionsrückgabe mit einer `As`\-Klausel zur Angabe des Datentyps deklariert werden, z. B. `Dim MyNum As Short`.  
  
 **Fehler\-ID:** BC30209  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob das `As`\-Schlüsselwort falsch geschrieben wurde.  
  
2.  Geben Sie eine `As`\-Klausel für die deklarierte Variable an, oder deaktivieren Sie `Option Strict Off`.  
  
## Siehe auch  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Variablendeklaration](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)