---
title: "Die Konstante &quot;&lt;Konstantenname&gt;&quot; kann nicht von ihrem eigenen Wert abh&#228;ngen | Microsoft Docs"
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
  - "bc30500"
  - "vbc30500"
helpviewer_keywords: 
  - "BC30500"
ms.assetid: 0dad89bc-9196-492f-acd9-7777757362f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Konstante &quot;&lt;Konstantenname&gt;&quot; kann nicht von ihrem eigenen Wert abh&#228;ngen
Sie haben eine zirkuläre Abhängigkeit im Code erstellt, wobei eine Konstante von ihrem eigenen Wert abhängt. Beispielsweise `Const a = Const b; Const b = Const a`.  
  
 **Fehler\-ID:** BC30500  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie den Code, um festzustellen, wo die Konstante ausgewertet wird, und ändern Sie sie entsprechend.  
  
## Siehe auch  
 [NICHT IM BUILD Übersicht über Konstanten](http://msdn.microsoft.com/de-de/5c7f57fb-48b2-4a2f-afee-79d8e3adf15b)