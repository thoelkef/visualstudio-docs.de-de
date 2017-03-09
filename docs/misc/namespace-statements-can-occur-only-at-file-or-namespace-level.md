---
title: "Namespace-Anweisungen k&#246;nnen nur auf Namespace- oder Dateiebene verwendet werden. | Microsoft Docs"
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
  - "bc30618"
  - "vbc30618"
helpviewer_keywords: 
  - "BC30618"
ms.assetid: bcd365a4-5d84-4c3c-83dc-40cb4c47f73b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace-Anweisungen k&#246;nnen nur auf Namespace- oder Dateiebene verwendet werden.
`Namespace`\-Anweisungen müssen nach `Option`\-Anweisungen, `Imports`\-Anweisungen und globalen Attributen angezeigt werden, aber vor allen anderen Deklarationen in der Quelldatei.  
  
 **Fehler\-ID:** BC30618  
  
### So beheben Sie diesen Fehler  
  
-   Verschieben Sie die `Namespace`\-Anweisung an den Anfang der Namespacedeklaration oder Quelldatei.  
  
## Siehe auch  
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Namespaces in Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)