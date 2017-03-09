---
title: "Die &lt;Methodenname&gt;-Methode hat nicht die gleiche Signatur wie der Delegat &quot;&lt;Delegatname&gt;&quot;. | Microsoft Docs"
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
  - "bc30408"
  - "vbc30408"
helpviewer_keywords: 
  - "BC30408"
ms.assetid: 845f6686-388f-4253-b635-146e517015a1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &lt;Methodenname&gt;-Methode hat nicht die gleiche Signatur wie der Delegat &quot;&lt;Delegatname&gt;&quot;.
Es gibt einen Konflikt zwischen den Signaturen der Methode und des Delegaten, die Sie verwenden möchten. Die `Delegate`\-Anweisung definiert die Parameter\- und Rückgabetypen einer Delegatklasse. Jede Prozedur mit passenden Parametern und Typen sowie passendem Rückgabetyp kann dazu verwendet werden, eine Instanz dieses Delegattyps zu erstellen. Jede Delegatklasse definiert einen Konstruktor, dem die Spezifikation einer Objektmethode übergeben wird.  
  
 **Fehler\-ID:** BC30408  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Signaturen, um den Konflikt zu finden und ihn zu korrigieren.  
  
## Siehe auch  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)