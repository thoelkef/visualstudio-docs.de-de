---
title: "Zu viele Typargumente f&#252;r &#39;&lt;generischer_Methodenname&gt;&#39;. | Microsoft Docs"
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
  - "bc32043"
  - "vbc32043"
helpviewer_keywords: 
  - "BC32043"
ms.assetid: c4d8f67a-4317-461a-9446-6717cfa1d888
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Zu viele Typargumente f&#252;r &#39;&lt;generischer_Methodenname&gt;&#39;.
Eine generische Methode wurde mit mehr Typargumenten aufgerufen, als Typparameter vorhanden sind.  
  
 Wenn Sie eine generische Methode aufrufen, müssen Sie für jeden von dieser Methode definierten Typparameter ein Typargument angeben.  
  
 **Fehler\-ID:** BC32043  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie Typargumente aus Ihrer Typargumentliste, sodass es für jeden von Typparameter der aufgerufenen generischen Methode genau ein Typargument gibt.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)