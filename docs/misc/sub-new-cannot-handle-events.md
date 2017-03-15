---
title: "&#39;Sub New&#39; kann keine Ereignisse behandeln. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; kann keine Ereignisse behandeln.
Sie haben versucht, `Sub New` mit `Handles` zu kombinieren. Dies ist ungültig. Verwenden Sie das `Handles`\-Schlüsselwort am Ende der Prozedurdeklaration, damit sie Ereignisse verarbeitet, die durch eine mithilfe des Schlüsselworts `WithEvents` deklarierte Objektvariable ausgelöst wurden.  
  
 **Fehler\-ID:** BC30497  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie in diesem Kontext nicht `New`.  
  
## Siehe auch  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)