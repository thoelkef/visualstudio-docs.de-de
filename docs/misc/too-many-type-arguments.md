---
title: "Zu viele Typargumente. | Microsoft Docs"
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
  - "vbc36579"
  - "bc36579"
helpviewer_keywords: 
  - "BC36579"
ms.assetid: f59617b2-ca66-45c6-baaa-3c8bdf7f9a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Zu viele Typargumente.
Eine generische Methode wurde mit mehr Typargumenten aufgerufen, als Typparameter vorhanden sind.  
  
 Wenn Sie eine generische Methode aufrufen, müssen Sie für jeden von dieser Methode definierten Typparameter ein Typargument angeben.  
  
 **Fehler\-ID:** BC36579  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie Typargumente aus Ihrer Typargumentliste, sodass es für jeden von Typparameter der aufgerufenen generischen Methode genau ein Typargument gibt.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)