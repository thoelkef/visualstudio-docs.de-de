---
title: "Operator kann nicht &#252;berladen werden. | Microsoft Docs"
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
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator kann nicht &#252;berladen werden.
Nur bestimmte Operatoren sind für Überladen geeignet. In der folgenden Tabelle sind die Operatoren aufgelistet, die Sie definieren können.  
  
|Typ|Operatoren|  
|---------|----------------|  
|Unär|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binär|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Konvertierung \(unär\)|`CType`|  
  
 Beachten Sie, dass der `=`\-Operator in der binären Liste nicht der Zuweisungsoperator, sondern der Vergleichsoperator ist.  
  
 **Fehler\-ID:** BC33002  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie einen Operator aus der Gruppe der überladbaren Operatoren aus.  
  
2.  Wenn Sie die Funktionalität des Überladens eines Operators benötigen, der nicht direkt überladen werden kann, erstellen Sie eine `Function`\-Prozedur, die die entsprechenden Parameter übernimmt und den entsprechenden Wert zurückgibt.  
  
## Siehe auch  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)