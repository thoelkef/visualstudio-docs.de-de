---
title: "Das Ereignis &quot;&lt;Ereignisname1&gt;&quot; kann das Ereignis &quot;&lt;Ereignisname2&gt;&quot; nicht implementieren, da der Delegattyp nicht mit dem Delegattyp eines anderen Ereignisses &#252;bereinstimmt, das von &quot;&lt;Ereignisname1&gt;&quot; implementiert wird | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Ereignis &quot;&lt;Ereignisname1&gt;&quot; kann das Ereignis &quot;&lt;Ereignisname2&gt;&quot; nicht implementieren, da der Delegattyp nicht mit dem Delegattyp eines anderen Ereignisses &#252;bereinstimmt, das von &quot;&lt;Ereignisname1&gt;&quot; implementiert wird
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kann ein Ereignis nicht implementieren, weil der Delegattyp des Ereignisses nicht mit dem Delegattyp eines anderen Ereignisses übereinstimmt. Dieser Fehler kann auftreten, wenn Sie mehrere Ereignisse in einer Schnittstelle definieren und anschließend versuchen, sie mit demselben Ereignis zu implementieren. Ein Ereignis kann zwei oder mehrere Ereignisse nur implementieren, wenn alle implementierten Ereignisse mit der `As`\-Syntax deklariert werden und denselben Delegattyp angeben.  
  
 **Fehler\-ID:** BC31407  
  
### So beheben Sie diesen Fehler  
  
-   Implementieren Sie die Ereignisse separat.  
  
## Siehe auch  
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)