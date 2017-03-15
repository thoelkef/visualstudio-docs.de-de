---
title: "&lt;Name1&gt; f&#252;r „Imports &lt;Name2&gt;“ verweist weder auf einen Namespace, noch auf eine Klasse, Struktur, Enumeration oder ein Modul. | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Name1&gt; f&#252;r „Imports &lt;Name2&gt;“ verweist weder auf einen Namespace, noch auf eine Klasse, Struktur, Enumeration oder ein Modul.
Sie haben versucht, die `Imports`\-Anweisung für ein Element zu verwenden, das keines der folgenden Objekte ist: `Namespace`, `Class`, `Structure`, `Enum` oder `Module`. Die `Imports`\-Anweisung importiert Namespacenamen aus referenzierten Projekten und Assemblys oder Namespacenamen, die im selben Projekt wie das Modul definiert sind, in dem die Anweisung erscheint.  
  
 **Fehler\-ID:** BC30467  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Entität, die Sie importieren möchten, und stellen Sie sicher, dass sie mit einer `Imports`\-Anweisung verwendet werden darf.  
  
## Siehe auch  
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)