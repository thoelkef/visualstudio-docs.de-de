---
title: "&quot;&lt;Spezifizierer&gt;&quot; ist in einer Membervariablendeklaration ung&#252;ltig. | Microsoft Docs"
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
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Spezifizierer&gt;&quot; ist in einer Membervariablendeklaration ung&#252;ltig.
Eine `Dim`\-Anweisung enthält ein ungültiges Schlüsselwort. Eine `Dim`\-Anweisung darf nur die Schlüsselwörter `Friend`, `Private`, `Protected`, `Public`, `ReadOnly`, `Shadows`, `Shared` oder `Static` enthalten.  
  
 Diese Meldung kann auch angezeigt werden, wenn Sie eine `Static`\-Variable außerhalb einer Prozedur deklarieren. Sie können `Static` nur auf Prozedurebene verwenden.  
  
 Beachten Sie, dass Sie das `Dim`\-Schlüsselwort optional weglassen können, wenn Sie ein gültiges Schlüsselwort in eine `Dim`\-Anweisung einfügen.  
  
 **Fehler\-ID:** BC30235  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das ungültige Schlüsselwort aus der `Dim`\-Anweisung.  
  
2.  Wenn Sie eine `Static`\-Variable außerhalb einer Prozedur deklariert haben, verschieben Sie die Deklaration entweder in eine Prozedur, oder entfernen Sie das `Static`\-Schlüsselwort.  
  
## Siehe auch  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)