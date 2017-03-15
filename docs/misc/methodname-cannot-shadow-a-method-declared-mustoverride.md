---
title: "&quot;&lt;Methodenname&gt;&quot; kann kein Shadowing f&#252;r eine Methode durchf&#252;hren, die als &quot;MustOverride&quot; deklariert ist | Microsoft Docs"
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
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Methodenname&gt;&quot; kann kein Shadowing f&#252;r eine Methode durchf&#252;hren, die als &quot;MustOverride&quot; deklariert ist
Eine Eigenschaft oder Methode mit dem `MustOverride`\-Modifizierer und dem gleichen Namen wird in einer abgeleiteten Klasse deklariert.  
  
 **Fehler\-ID:** BC31404  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie den `Overrides`\-Modifizierer der überschreibenden Eigenschaft oder Methode in der abgeleiteten Klasse hinzu.  
  
2.  Entfernen Sie den `MustOverride`\-Modifizierer aus der Eigenschaft oder Methode in der Basisklasse.  
  
## Siehe auch  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)