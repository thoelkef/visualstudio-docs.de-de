---
title: "Enumerationstypen k&#246;nnen keine NULL-Werte zulassen | Microsoft Docs"
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
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Enumerationstypen k&#246;nnen keine NULL-Werte zulassen
Der zugrunde liegende Typ, der verwendet wird, um eine Enumeration zu deklarieren, kann keine NULL\-Werte zulassen. Beispielsweise verursacht der folgende Code diesen Fehler:  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **Fehler\-ID:** BC32129  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie in einer `Enum`\-Deklaration keinen zugrunde liegenden Typ, der keine NULL\-Werte zulassen kann.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Enum Statement](/dotnet/visual-basic/language-reference/statements/enum-statement)