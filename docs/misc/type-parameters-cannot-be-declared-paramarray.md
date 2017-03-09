---
title: "&lt;Typ&gt;-Parameter k&#246;nnen nicht als „ParamArray“ deklariert werden. | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Typ&gt;-Parameter k&#246;nnen nicht als „ParamArray“ deklariert werden.
Eine Definition eines Delegaten, Ereignisses oder Operators deklariert einen [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)\-Parameter.  
  
 `ParamArray`\-Parameter sind nur für `Declare`\-, `Function`\-, `Property`\- und `Sub`\-Parameter gestattet.  
  
 **Fehler\-ID:** BC33009  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `ParamArray`\-Schlüsselwort aus der Parameterliste.  
  
-   Wenn Sie einen Operator definieren, können Sie möglicherweise die `ParamArray`\-Funktionalität durch eine Reihe von Überladungen erreichen.  
  
-   Wenn Sie einen Delegaten oder ein Ereignis definieren, müssen Sie die Gesamtlogik dieses Teils der Anwendung überarbeiten. Sie können keine [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)\- oder `ParamArray`\-Parameter oder überladene Versionen für Delegat\- oder Ereignisparameter verwenden.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)