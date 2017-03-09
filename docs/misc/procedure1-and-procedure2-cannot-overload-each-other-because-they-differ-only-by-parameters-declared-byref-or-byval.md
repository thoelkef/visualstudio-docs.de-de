---
title: "&#39;&lt;Prozedur1&gt;&#39; und &#39;&lt;Prozedur2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch Parameter unterscheiden, die als „ByRef“ oder „ByVal“ deklariert sind. | Microsoft Docs"
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
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Prozedur1&gt;&#39; und &#39;&lt;Prozedur2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch Parameter unterscheiden, die als „ByRef“ oder „ByVal“ deklariert sind.
'\<Prozedur1\>' und '\<Prozedur2\>' können sich nicht gegenseitig überladen, da sie sich nur durch Parameter unterscheiden, die als „ByRef“ oder „ByVal“ deklariert sind. „Shadows“ wird angenommen.  
  
 Zwei Prozedurdeklarationen geben denselben Namen und dieselbe Argumentliste an, und der einzige Unterschied besteht in der Spezifikation von `ByRef` oder `ByVal` für eines oder mehrere der Argumente. Überladene Versionen einer Prozedur müssen hinsichtlich Anzahl, Reihenfolge oder Datentypen der Argumente voneinander abweichen.  
  
 Diese Meldung ist eine Warnung.`Shadows` wird standardmäßig angenommen. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42003  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie beabsichtigen, eine Reihe von überladenen Versionen einer Prozedur zu erstellen, verwenden Sie für jede Version eine unterschiedliche Anzahl, Reihenfolge bzw. verschiedene Datentypen der Argumente. Fügen Sie außerdem das `Overloads`\-Schlüsselwort zu jeder Deklaration hinzu.  
  
-   Wenn Sie nicht beabsichtigen, eine Prozedur zu überladen, ändern Sie den Namen der Prozedur in einer der Deklarationen.  
  
## Siehe auch  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)