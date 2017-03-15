---
title: "&lt;name&gt; is not a valid solution name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALIDSOLUTIONNAME"
  - "vs.message.0x800A00D3"
ms.assetid: 79b7870d-16bd-4527-8ce6-ffb015e7e330
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid solution name.
Im Allgemeinen tritt dieser Fehler auf, wenn der Befehl `File.NewProject` im **Befehlsfenster** oder im Feld **Suchen** mit einem falsch formatierten Wert für das Argument \/sln:*solutionname* eingegeben wurde.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie die Befehlssyntax erneut und ohne das optionale Argument \/sln:*solutionname* ein.  Es wird automatisch ein eindeutiger Projektmappenname generiert.  
  
     – oder –  
  
     Stellen Sie sicher, dass der Projektmappenname keine führenden bzw. nachstehenden Leerzeichen enthält und kein reserviertes Wort ist.  Reservierte Wörter sind u. a. NUL, CON, AUX, COM*x* und LPT*x*, wobei *x* eine ganze Zahl von 1 bis 9 ist.  
  
## Siehe auch  
 [Befehlsfenster](../ide/reference/command-window.md)