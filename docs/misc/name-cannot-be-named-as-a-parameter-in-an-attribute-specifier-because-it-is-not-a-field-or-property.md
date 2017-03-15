---
title: "&#39;&lt;Name&gt;&#39; kann nicht als Parameter in einem Attributspezifizierer verwendet werden, da er kein Feld bzw. keine Eigenschaft ist. | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32010"
  - "bc32010"
helpviewer_keywords: 
  - "BC32010"
ms.assetid: bfa68729-71ea-410e-bef1-83a7dab44d2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Name&gt;&#39; kann nicht als Parameter in einem Attributspezifizierer verwendet werden, da er kein Feld bzw. keine Eigenschaft ist.
Ein Attributblock legt einen Wert für einen nicht variablen Member des Attributs fest. Sie können Werte nur zu variablen Membern wie Feldern oder Eigenschaften zuweisen.  
  
 **Fehler\-ID:** BC32010  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass die Attribut\- und Membernamen richtig geschrieben sind.  
  
2.  Entfernen Sie das Argument aus dem Attributblock, wenn der Member nicht variabel ist.  
  
## Siehe auch  
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)