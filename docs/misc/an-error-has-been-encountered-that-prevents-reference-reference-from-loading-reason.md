---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
Ein schwerwiegender Fehler ist aufgetreten, als ein Verweis von der Projektdatei entfernt wurde.  Ursachen für diesen Fehler werden unter \<Ursache\> beschrieben. Dazu gehören:  
  
-   Falsch formatierte GUID für einen Verweis.  Dies trifft nur auf COM\-Verweise zu.  
  
-   Fehlerhaftes Wrappertool.  Zur Zeit kann die Wrappertool\-Eigenschaft entweder **tlbimp**, **aximp** oder **primary** sein.  Dies trifft nur auf COM\-Verweise zu.  
  
-   Fehlerhafte Projektverweiszeichenfolge.  Dies trifft nur auf Verweise von Projekt auf Projekt zu.  
  
 **So beheben Sie diesen Fehler**  
  
-   Fügen Sie dem Projekt den Verweis hinzu, um diesen Fehler zu beheben.  
  
     Verweise, für die diese Diagnose angezeigt wird, werden nicht in das Projekt geladen.  
  
## Siehe auch  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)