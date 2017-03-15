---
title: "Ereignisse in Schnittstellen k&#246;nnen nicht als &#39;&lt;implements&gt;&#39; deklariert werden. | Microsoft Docs"
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
  - "bc30688"
  - "vbc30688"
helpviewer_keywords: 
  - "BC30688"
ms.assetid: 577823c1-815c-4f1c-9177-4bbf73fa92db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ereignisse in Schnittstellen k&#246;nnen nicht als &#39;&lt;implements&gt;&#39; deklariert werden.
In Schnittstellen deklarierte Ereignisse können nicht die Ereignisse anderer Schnittstellen implementieren.  
  
 **Fehler\-ID:** BC30688  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `Implements`\-Anweisung.  
  
2.  Implementieren Sie das Ereignis innerhalb einer Klasse oder Struktur.  
  
## Siehe auch  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)