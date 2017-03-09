---
title: "&quot;Option Strict On&quot; erfordert in allen Methodenparametern eine As-Klausel. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; erfordert in allen Methodenparametern eine As-Klausel.
Eine Methode enthält einen Parameter ohne eine `As`\-Klausel. Wenn `Option Strict` aktiviert ist, muss jede Variable, jede Eigenschaft, jedes Prozedurargument und jede Funktionsrückgabe mit einer `As`\-Klausel zur Angabe des Datentyps deklariert werden, z. B. `Sub GetData(ByVal filter As String)`.  
  
 **Fehler\-ID:** BC30211  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen, ob das `As`\-Schlüsselwort falsch geschrieben ist.  
  
-   Geben Sie eine `As`\-Klausel für die deklarierte Variable an, oder deaktivieren Sie `Option Strict`.  
  
## Siehe auch  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)