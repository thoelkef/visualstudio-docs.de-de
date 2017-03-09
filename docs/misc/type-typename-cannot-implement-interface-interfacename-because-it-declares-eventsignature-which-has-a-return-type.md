---
title: "Der Typ &lt;Typname&gt; kann die Schnittstelle &lt;Schnittstellenname&gt; nicht implementieren, weil eine &lt;Ereignissignatur&gt; deklariert wird, die &#252;ber einen R&#252;ckgabetyp verf&#252;gt. | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &lt;Typname&gt; kann die Schnittstelle &lt;Schnittstellenname&gt; nicht implementieren, weil eine &lt;Ereignissignatur&gt; deklariert wird, die &#252;ber einen R&#252;ckgabetyp verf&#252;gt.
Eine Klasse oder Struktur versucht, eine Schnittstelle zu implementieren, die ein Ereignis deklariert, das einen Wert zurückgibt.  
  
 Visual Basic unterstützt das Deklarieren von Ereignissen, die Werte zurückgeben, derzeit nicht.  
  
 **Fehler\-ID:** BC30945  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Implements`\-Anweisung aus der Klassen\- oder Strukturdefinition, oder implementieren Sie eine andere Schnittstelle.  
  
## Siehe auch  
 [NICHT IM BUILD: Ereignisse und Ereignishandler](http://msdn.microsoft.com/de-de/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be)