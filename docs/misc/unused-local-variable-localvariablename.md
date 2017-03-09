---
title: "Nicht verwendete lokale Variable: &quot;&lt;localvariablename&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nicht verwendete lokale Variable: &quot;&lt;localvariablename&gt;&quot;
Eine lokale Variable in einer Prozedur wird deklariert, aber nie verwendet.  
  
 Eine Möglichkeit besteht darin, dass eine der lokalen Variablen in der Prozedur falsch geschrieben wurde. Wenn diese Variable tatsächlich in einer anderen Anweisung verwendet wird, aber anders geschrieben ist, geht der Compiler davon aus, dass es sich um zwei unterschiedliche Variablen handelt.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42024  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der lokalen Variablen in der Prozedur. Beachten Sie, dass nicht zwischen Groß\-und Kleinschreibung unterschieden wird. Die Namen `ABC` und `abc` verweisen auf dieselbe Variable.  
  
2.  Wenn keine Rechtschreibfehler vorhanden ist, entfernen Sie die Deklaration dieser Variablen, oder verwenden Sie sie in einer anderen Anweisung in der Prozedur.  
  
## Siehe auch  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)