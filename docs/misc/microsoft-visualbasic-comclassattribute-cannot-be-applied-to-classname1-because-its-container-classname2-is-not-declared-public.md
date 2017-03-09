---
title: "&quot;Microsoft.VisualBasic.ComClassAttribute&quot; kann nicht auf &quot;&lt;Klassenname1&gt;&quot; angewendet werden, da sein Container &quot;&lt;Klassenname2&gt;&quot; nicht als &quot;Public&quot; deklariert ist. | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Microsoft.VisualBasic.ComClassAttribute&quot; kann nicht auf &quot;&lt;Klassenname1&gt;&quot; angewendet werden, da sein Container &quot;&lt;Klassenname2&gt;&quot; nicht als &quot;Public&quot; deklariert ist.
Eine Klasse mit einem `COMClassAttribute`\-Attributblock ist innerhalb einer Klasse deklariert, die nicht als `Public` deklariert ist. Wenn eine Klasse als COM\-Objekt verfügbar gemacht werden soll, muss die gesamte Kapselungshierarchie mit `Public`\-Zugriff deklariert werden.  
  
 **Fehler\-ID:** BC32504  
  
### So beheben Sie diesen Fehler  
  
-   Deklarieren Sie alle enthaltenden Klassen als `Public`, oder entfernen Sie den `COMClassAttribute`\-Attributblock.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute\-Klasse](http://msdn.microsoft.com/de-de/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)