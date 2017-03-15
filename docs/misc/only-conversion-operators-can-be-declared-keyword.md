---
title: "Nur Konvertierungsoperatoren k&#246;nnen als &#39;&lt;schl&#252;sselwort&gt;&#39; deklariert werden. | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nur Konvertierungsoperatoren k&#246;nnen als &#39;&lt;schl&#252;sselwort&gt;&#39; deklariert werden.
Ein [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) gibt [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) oder [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) an, obwohl es sich bei dem Operator nicht um einen Konversionsoperator handelt.  
  
 Jeder Operator muss sowohl als [Public](/dotnet/visual-basic/language-reference/modifiers/public) als auch als [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) deklariert werden. Jedoch können nur Konversionsoperatoren als [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) oder [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) deklariert werden, nicht jedoch beides.  
  
 Eine Operatordefinition kann optional die Schlüsselwörter [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) und [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) enthalten. Keine anderen Schlüsselwörter sind in einem [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) zulässig.  
  
 **Fehler\-ID:** BC33019  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das `Widening`\- oder `Narrowing`\-Schlüsselwort aus der Operatordefinition. Diese gelten nicht, da keine Typkonvertierung stattfindet.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)