---
title: "&quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da er kein System.AttributeUsageAttribute-Attribut enth&#228;lt. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31505"
  - "bc31505"
helpviewer_keywords: 
  - "BC31505"
ms.assetid: 7dd84c9d-6711-4dab-afc6-1fe4dee78051
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da er kein System.AttributeUsageAttribute-Attribut enth&#228;lt.
Es wurde versucht, die Verwendung eines Attributs zu definieren, das ohne `System.AttributeUsageAttribute` deklariert wurde.  
  
 **Fehler\-ID:** BC31505  
  
### So beheben Sie diesen Fehler  
  
1.  Benutzerdefinierte Attribute müssen Klassen sein, die von `System.Attribute` abgeleitet werden und auf die das `AttributeUsageAttribute`\-Attribut angewendet wurde.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)