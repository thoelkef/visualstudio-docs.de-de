---
title: "Methoden oder Ereignisse, die Schnittstellenmember implementieren, k&#246;nnen nicht als &quot;Shared&quot; deklariert werden. | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methoden oder Ereignisse, die Schnittstellenmember implementieren, k&#246;nnen nicht als &quot;Shared&quot; deklariert werden.
Sie haben versucht, eine Methode oder ein Ereignis, das einen Schnittstellenmember implementiert, als `Shared` zu deklarieren. Methoden und Ereignisse, die in einer Klasse implementiert werden, können nur in einer nicht vererbbaren Klasse als `Shared` oder `Private` festgelegt werden.  
  
 **Fehler\-ID:** BC30505  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Schlüsselwort "`Shared`".  
  
## Siehe auch  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)