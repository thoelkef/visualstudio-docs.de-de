---
title: "Zu viele Typargumente f&#252;r die in &lt;Typname&gt; definierte Erweiterungsmethode &lt;Methodename&gt; | Microsoft Docs"
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
  - "bc36591"
  - "vbc36591"
helpviewer_keywords: 
  - "BC36591"
ms.assetid: 504c9b1f-f511-4198-8970-136d1a1bdafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Zu viele Typargumente f&#252;r die in &lt;Typname&gt; definierte Erweiterungsmethode &lt;Methodename&gt;
Eine generische Erweiterungsmethode wurde mit mehr Typargumenten aufgerufen, als Typparameter vorhanden sind.  
  
 Wenn Sie eine generische Methode aufrufen, müssen Sie für jeden von dieser Methode definierten Typparameter ein Typargument angeben.  
  
 **Fehler\-ID:** BC36591  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie Typargumente aus Ihrer Typargumentliste, sodass es für jeden von der aufgerufenen generischen Methode definierten Typparameter genau ein Typargument gibt.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)