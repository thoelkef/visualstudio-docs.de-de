---
title: "&quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da es MustOverride-Methoden enth&#228;lt, die nicht &#252;berschrieben wurden. | Microsoft Docs"
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
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da es MustOverride-Methoden enth&#228;lt, die nicht &#252;berschrieben wurden.
Klassen mit `MustOverride`\-Methoden können nicht als Attribute verwendet werden.  
  
 `MustOverride`\-Member von Attributklassen können nur von abgeleiteten Klassen verwendet werden, die solche Member überschreiben.  
  
 **Fehler\-ID:** BC31507  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den `MustOverride`\-Modifizierer aus Attributklassenmembern.  
  
2.  Implementieren Sie `MustOverride`\-Member in einer abgeleiteten Klasse, und verwenden Sie diese Klasse als Attribut.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)