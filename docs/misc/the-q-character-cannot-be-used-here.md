---
title: "An dieser Stelle darf das Fragezeichen (?) nicht verwendet werden. | Microsoft Docs"
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
  - "bc36637"
  - "vbc36637"
helpviewer_keywords: 
  - "BC36637"
ms.assetid: a54c46e7-8fd8-4941-9fce-72f2b41b5e24
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# An dieser Stelle darf das Fragezeichen (?) nicht verwendet werden.
Das Fragezeichen \(?\) kann verwendet werden, um anzugeben, dass ein Werttyp oder eine Struktur NULL\-Werte zulässt. Die Verwendung in anderen Fällen ist eingeschränkt. Der folgende Code generiert beispielsweise diese Ausnahme.  
  
```  
' Not valid. ' #Const found = True?  
```  
  
 **Fehler\-ID:** BC36637  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Fragezeichen \(?\) aus der Deklaration.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)