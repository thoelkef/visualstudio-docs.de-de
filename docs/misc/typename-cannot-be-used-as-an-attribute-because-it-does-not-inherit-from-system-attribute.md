---
title: "&quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da es nicht von &quot;System.Attribute&quot; erbt | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da es nicht von &quot;System.Attribute&quot; erbt
Es wurde versucht, eine Klasse zu verwenden, die nicht von `System.Attribute` abgeleitet ist.  
  
 **Fehler\-ID:** BC31504  
  
### So beheben Sie diesen Fehler  
  
1.  Definieren Sie benutzerdefinierte Attribute als von `System.Attribute` abgeleitete Klassen, indem Sie der ersten Codezeile in der Klasse eine `Imports`\-Anweisung hinzufügen.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)