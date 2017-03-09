---
title: "Typargumente k&#246;nnen nicht auf den Ausdruck &quot;&lt;Ausdruck&gt;&quot; angewendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typargumente k&#246;nnen nicht auf den Ausdruck &quot;&lt;Ausdruck&gt;&quot; angewendet werden
Ein Importalias wurde mit einer [Of](/dotnet/visual-basic/language-reference/statements/of-clause)\-Klausel definiert, die Typargumente an den Importalias übergibt.  
  
 Typargumente werden für generische Typen verwendet, und nur Klassen, Strukturen, Schnittstellen, Prozeduren und Delegaten können generisch sein. Weder Namespaces noch Importaliase können generisch sein.  
  
 **Fehler\-ID:** BC32058  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Of`\-Klausel und ihre Typargumente aus dem Importalias.  
  
## Siehe auch  
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)