---
title: "Eine Eigenschaft, die als &quot;ReadOnly&quot; deklariert ist, darf kein &quot;Set&quot; haben. | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Eigenschaft, die als &quot;ReadOnly&quot; deklariert ist, darf kein &quot;Set&quot; haben.
Die `Set`\-Prozedur schreibt den Wert einer Eigenschaft. In `ReadOnly`\-Eigenschaften kann nicht geschrieben werden.  
  
 **Fehler\-ID:** BC30022  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Schlüsselwort "`ReadOnly`" aus der `Property`\-Anweisung, oder entfernen Sie die `Set`\-Prozedur aus dem Eigenschaftentext.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)