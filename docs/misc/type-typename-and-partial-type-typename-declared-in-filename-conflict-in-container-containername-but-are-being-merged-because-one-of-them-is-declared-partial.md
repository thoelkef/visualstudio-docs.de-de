---
title: "Typ &quot;&lt;Typname&gt;&quot; und Typ &quot;&lt;Typname&gt;&quot; (partiell, in &quot;&lt;Dateiname&gt;&quot; deklariert) verursachen einen Konflikt in Container &quot;&lt;Containername&gt;&quot;, werden jedoch zusammengef&#252;hrt, da eines der Elemente als partiell deklariert ist. | Microsoft Docs"
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
  - "vbc40047"
  - "bc40047"
helpviewer_keywords: 
  - "BC40047"
ms.assetid: 05f62dd9-f97d-4893-8904-76ecd2da474c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typ &quot;&lt;Typname&gt;&quot; und Typ &quot;&lt;Typname&gt;&quot; (partiell, in &quot;&lt;Dateiname&gt;&quot; deklariert) verursachen einen Konflikt in Container &quot;&lt;Containername&gt;&quot;, werden jedoch zusammengef&#252;hrt, da eines der Elemente als partiell deklariert ist.
Eine Klasse oder Struktur ist in mehreren Definitionen desselben Containertyps enthalten, und mindestens zwei Definitionen sind nicht als `Partial` gekennzeichnet.  
  
 Sie müssen das [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)\-Schlüsselwort für mindestens eine der Definitionen einer Klasse oder Struktur verwenden, allerdings empfiehlt es sich, das Schlüsselwort für alle partiellen Definitionen zu verwenden.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40047  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie das [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)\-Schlüsselwort für jede partielle Definition der Klasse oder Struktur.