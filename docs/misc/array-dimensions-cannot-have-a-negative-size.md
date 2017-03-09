---
title: "Arraydimensionen k&#246;nnen keine negative Gr&#246;&#223;e haben | Microsoft Docs"
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
  - "bc30611"
  - "vbc30611"
helpviewer_keywords: 
  - "BC30611"
ms.assetid: e310bd0d-f221-4b02-87f3-02124f4de87c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arraydimensionen k&#246;nnen keine negative Gr&#246;&#223;e haben
Mindestens eine der festgelegten Arraygrenzen ist eine negative Zahl. Ein negativer Index kann nur angegeben werden, wenn eine Obergrenze von \-1 verwendet wird, um ein leeres Array zu deklarieren. Ein solches Array enthält null Elemente, aber es ist nicht `Nothing`.  
  
 **Fehler\-ID:** BC30611  
  
### So beheben Sie diesen Fehler  
  
-   Ersetzen Sie die negative Arraygrenze durch eine positive Zahl.  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)