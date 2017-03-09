---
title: "Lokale Variablen innerhalb von Methoden von Strukturen k&#246;nnen nicht als &quot;Static&quot; deklariert werden | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lokale Variablen innerhalb von Methoden von Strukturen k&#246;nnen nicht als &quot;Static&quot; deklariert werden
Der `Static`\-Modifizierer kann nicht mit lokalen Variablen in Strukturen verwendet werden.  
  
 **Fehler\-ID:** BC31400  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den `Static`\-Modifizierer aus der lokalen Variablen.  
  
2.  Deklarieren Sie die Variable als statische Variable mit einem größeren Bereich.  
  
## Siehe auch  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)