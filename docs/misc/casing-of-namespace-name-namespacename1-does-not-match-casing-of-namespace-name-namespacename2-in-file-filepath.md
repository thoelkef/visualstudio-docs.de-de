---
title: "Die Gro&#223;-/Kleinschreibung des Namespacenamens &#39;&lt;namespacename1&gt;&#39; stimmt nicht mit der Gro&#223;-/Kleinschreibung des Namespacenamens &#39;&lt;namespacename2&gt;&#39; in der Datei &#39;&lt;dateipfad&gt;&#39; &#252;berein | Microsoft Docs"
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
  - "vbc40055"
  - "bc40055"
helpviewer_keywords: 
  - "BC40055"
ms.assetid: adaac2fe-1513-4234-afe7-633a76089f36
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Gro&#223;-/Kleinschreibung des Namespacenamens &#39;&lt;namespacename1&gt;&#39; stimmt nicht mit der Gro&#223;-/Kleinschreibung des Namespacenamens &#39;&lt;namespacename2&gt;&#39; in der Datei &#39;&lt;dateipfad&gt;&#39; &#252;berein
Ein Namespace tritt mehrfach im Projekt auf, jedoch mit unterschiedlicher Groß\-\/Kleinschreibung.  
  
 *Schreibweise* bezieht sich auf die Verwendung von Groß\- und Kleinbuchstaben im Namen eines Programmierelements. Visual Basic unterscheidet Groß\- und Kleinschreibung nicht, die CLR \(Common Language Runtime\) jedoch wohl. Weitere Informationen finden Sie unter "Groß\- und Kleinschreibung in Namen" in [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40055  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie als Vorsichtsmaßnahme bei jedem Verweis auf einen Namespace immer die gleiche Groß\-\/Kleinschreibung. Dadurch wird die Fehlinterpretation durch die Common Language Runtime verhindert.  
  
## Siehe auch  
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Namespaces in Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)