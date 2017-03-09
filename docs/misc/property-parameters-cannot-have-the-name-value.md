---
title: "Eigenschaftenparameter k&#246;nnen nicht den Namen &#39;Value&#39; haben. | Microsoft Docs"
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
  - "bc32201"
  - "vbc32201"
helpviewer_keywords: 
  - "BC32201"
ms.assetid: ea720bc3-51e8-45fb-874c-f8cec9a250ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eigenschaftenparameter k&#246;nnen nicht den Namen &#39;Value&#39; haben.
Einem Parameter in einer `Property`\-Anweisung wurde die Bezeichnung `Value` zugewiesen. Dieser Name ist innerhalb einer Eigenschaftendefinition für den neuen Wert reserviert, der der Eigenschaft in der `Set`\-Prozedur zugewiesen wird.  
  
 **Fehler\-ID:** BC32201  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Namen des Parameters in der `Property`\-Anweisung.  
  
## Siehe auch  
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)