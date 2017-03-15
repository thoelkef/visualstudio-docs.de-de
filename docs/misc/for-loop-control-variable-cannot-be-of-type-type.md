---
title: "Die Steuerungsvariable der For-Schleife darf nicht vom Typ &quot;&lt;Typ&gt;&quot; sein. | Microsoft Docs"
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
  - "vbc30337"
  - "bc30337"
helpviewer_keywords: 
  - "BC30337"
ms.assetid: 988bba15-e9a2-4045-98a0-7f53c8b2c3e3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Steuerungsvariable der For-Schleife darf nicht vom Typ &quot;&lt;Typ&gt;&quot; sein.
Sie haben versucht, eine Schleifensteuerungsvariable zu verwenden, die einen ungültigen Typ aufweist. Am Anfang einer `For`\-Schleife werden Startpunkt, Endpunkt und Step\-Wert in der Reihenfolge ausgewertet, in der sie im Text auftreten. Alle drei Ausdrücke müssen implizit in den Typ der Variablen konvertiert werden. Wenn die `For`\-Schleifenvariable den Typ `Object` aufweist, muss mindestens einer der Ausdrücke zur Laufzeit einen numerischen Typ aufweisen, und alle drei Ausdrücke müssen in den umfassendsten numerischen Typ umwandelbar sein.  
  
 **Fehler\-ID:** BC30337  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie den Typ der Schleifensteuerungsvariablen, und ändern Sie ihn in einen gültigen Typ.  
  
## Siehe auch  
 [For \(Visual Basic\)](http://msdn.microsoft.com/de-de/c470a263-9b49-4308-8fd6-8592b84a7980)   
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)   
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)