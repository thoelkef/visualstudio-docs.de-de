---
title: "Der Attributmember &#39;&lt;Membername&gt;&#39; kann nicht das Ziel einer Zuweisung sein, da er nicht als &#39;Public&#39; deklariert ist. | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Attributmember &#39;&lt;Membername&gt;&#39; kann nicht das Ziel einer Zuweisung sein, da er nicht als &#39;Public&#39; deklariert ist.
Es wurde versucht, einem privaten Member eines Attributs einen Wert zuzuweisen.  
  
 **Fehler\-ID:** BC31511  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Zuweisung.  
  
2.  Wenn Sie selbst entwickelte benutzerdefinierte Attribute verwenden, ändern Sie den Zugriffsmodifizierer des Attributmembers in `Public`.  
  
## Siehe auch  
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)