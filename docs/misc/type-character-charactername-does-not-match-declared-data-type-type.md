---
title: "Das Typzeichen &quot;&lt;Zeichenname&gt;&quot; entspricht nicht dem deklarierten Datentyp &quot;&lt;Typ&gt;&quot;. | Microsoft Docs"
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
  - "vbc30277"
  - "bc30277"
helpviewer_keywords: 
  - "BC30277"
ms.assetid: 9808f57e-a46c-43f9-b5e7-275794627763
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Typzeichen &quot;&lt;Zeichenname&gt;&quot; entspricht nicht dem deklarierten Datentyp &quot;&lt;Typ&gt;&quot;.
Eine Variable wird mit einem Datentyp deklariert, aber der Verweis erfolgt über ein Typzeichen, das einen inkompatiblen Datentyp darstellt, z. B. `K$ = 10`, wenn `K` als `Integer` deklariert ist.  
  
 **Fehler\-ID:** BC30277  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den deklarierten Datentyp der Variablen, oder ändern bzw. entfernen Sie das Typzeichen im Verweis.  
  
## Siehe auch  
 [Type Characters](/dotnet/visual-basic/programming-guide/language-features/data-types/type-characters)