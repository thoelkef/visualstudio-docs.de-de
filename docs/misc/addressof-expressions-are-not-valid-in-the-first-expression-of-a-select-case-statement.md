---
title: "&#39;AddressOf&#39;-Ausdr&#252;cke sind im ersten Ausdruck einer &#39;Select Case&#39;-Anweisung nicht g&#252;ltig. | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39;-Ausdr&#252;cke sind im ersten Ausdruck einer &#39;Select Case&#39;-Anweisung nicht g&#252;ltig.
Sie können einen `AddressOf`\-Ausdruck nicht für den Testausdruck in einer `Select Case`\-Anweisung verwenden.`AddressOf`\-Ausdrücke geben Funktionsdelegate zurück, und der Testausdruck einer `Select Case`\-Anweisung muss ein elementarer Datentyp sein.  
  
 **Fehler\-ID:** BC36636  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie den Code, um festzustellen, ob eine andere bedingte Konstruktion für Sie geeignet wäre, z. B. eine `If...Then...Else`\-Anweisung.  
  
## Siehe auch  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)