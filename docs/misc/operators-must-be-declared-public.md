---
title: "Operatoren m&#252;ssen als &quot;Public&quot; deklariert werden. | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operatoren m&#252;ssen als &quot;Public&quot; deklariert werden.
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) enthält kein [Public](/dotnet/visual-basic/language-reference/modifiers/public)\-Schlüsselwort.  
  
 Eine `Operator`\-Prozedur erfordert sowohl das `Public`\-Schlüsselwort als auch das [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)\-Schlüsselwort, und ein Konvertierungsoperator erfordert auch entweder das [Widening](/dotnet/visual-basic/language-reference/modifiers/widening)\-Schlüsselwort oder das [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing)\-Schlüsselwort.  
  
 **Fehler\-ID:** BC33011  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie der `Operator`\-Anweisung das `Public`\-Schlüsselwort hinzu.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)