---
title: "&quot;&lt;Member&gt;&quot;, implizit f&#252;r &quot;&lt;Ereignisname&gt;&quot; definiert, kann kein Shadowing f&#252;r eine &quot;MustOverride&quot;-Methode in der Basisklasse &quot;&lt;Klassenname&gt;&quot; durchf&#252;hren | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Member&gt;&quot;, implizit f&#252;r &quot;&lt;Ereignisname&gt;&quot; definiert, kann kein Shadowing f&#252;r eine &quot;MustOverride&quot;-Methode in der Basisklasse &quot;&lt;Klassenname&gt;&quot; durchf&#252;hren
Das angegebene Ereignis deklariert einen Member mit demselben Namen implizit als eine Methode, die mit dem `MustOverride`\-Modifizierer deklariert wird.  
  
 **Fehler\-ID:** BC31413  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den `MustOverride`\-Modifizierer aus der Methode in der Basisklasse, oder weisen Sie der Eigenschaft oder der Methode einen eindeutigen Namen zu.  
  
## Siehe auch  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)