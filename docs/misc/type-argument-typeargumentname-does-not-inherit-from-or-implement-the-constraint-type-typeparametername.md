---
title: "Das Typargument &#39;&lt;Typargumentname&gt;&#39; erbt nicht vom Einschr&#228;nkungstyp &#39;&lt;Typparametername&gt;&#39; bzw. implementiert diesen nicht. | Microsoft Docs"
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
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Typargument &#39;&lt;Typargumentname&gt;&#39; erbt nicht vom Einschr&#228;nkungstyp &#39;&lt;Typparametername&gt;&#39; bzw. implementiert diesen nicht.
Ein für einen generischen Typ angegebenes Typargument entspricht nicht der Vererbungs\- oder Implementierungseinschränkung für den entsprechenden Typparameter.  
  
 Eine Einschränkungsliste erzwingt Anforderungen an das Typargument, das an den Typparameter übergeben wird. Die möglichen Anforderungen umfassen Folgendes:  
  
-   Das Typargument muss mindestens eine Schnittstelle implementieren.  
  
-   Das Typargument darf von höchstens einer Klasse erben.  
  
 Sie können die zuvor genannten Anforderungen für einen einzelnen Typparameter kombinieren.[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kann den Typ nicht erstellen, es sei denn, der Code stellt Typargumente bereit, die jede Einschränkung für jeden Typparameter erfüllen, der für den generischen Typ definiert ist.  
  
 **Fehler\-ID:** BC32044  
  
### So beheben Sie diesen Fehler  
  
-   Wählen Sie ein Typargument eines Typs aus, der jede für den Typparameter angegebene Schnittstelle implementiert und ggf. von der angegebenen Klasse erbt.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Gewusst wie: Verwenden einer generischen Klasse](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)