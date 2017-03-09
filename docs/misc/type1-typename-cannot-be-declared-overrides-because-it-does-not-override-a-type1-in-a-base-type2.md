---
title: "&lt;Typ1&gt; &quot;&lt;Typname&gt;&quot; kann nicht als &quot;Overrides&quot; deklariert werden, da er &lt;Typ1&gt; in einer Basis&lt;Typ2&gt; nicht &#252;berschreibt. | Microsoft Docs"
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
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Typ1&gt; &quot;&lt;Typname&gt;&quot; kann nicht als &quot;Overrides&quot; deklariert werden, da er &lt;Typ1&gt; in einer Basis&lt;Typ2&gt; nicht &#252;berschreibt.
Eine `Sub`\-, `Function`\- oder `Property`\-Anweisung gibt `Overrides`an, wenn kein Typ mit dem gleichen Namen in einer Basisklasse vorhanden ist.  
  
 **Fehler\-ID:** BC30284  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Typname richtig geschrieben wurde.  
  
2.  Entfernen Sie das überflüssige `Overrides`\-Schlüsselwort.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)