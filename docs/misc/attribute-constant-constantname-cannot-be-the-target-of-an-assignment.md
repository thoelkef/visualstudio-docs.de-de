---
title: "Die Attributkonstante &quot;&lt;Konstantenname&gt;&quot; kann nicht das Ziel einer Zuweisung sein. | Microsoft Docs"
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
  - "bc31510"
  - "vbc31510"
helpviewer_keywords: 
  - "BC31510"
ms.assetid: 5459c531-3a4e-4e03-b185-9c5766254982
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Attributkonstante &quot;&lt;Konstantenname&gt;&quot; kann nicht das Ziel einer Zuweisung sein.
Es wurde versucht, einer Konstanten, die in einem Attribut deklariert ist, einen Wert zuzuweisen.  
  
 **Fehler\-ID:** BC31510  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die fehlerhafte Zuweisung.  
  
-   Wenn Sie benutzerdefinierte Attribute verwenden, die Sie entwickelt haben, definieren Sie den Member im Attribut neu als Feld.  
  
## Siehe auch  
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Constants and Enumerations](/dotnet/visual-basic/language-reference/constants-and-enumerations)