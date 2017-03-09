---
title: "Operator ohne As-Klausel; Typ &quot;Object&quot; wird angenommen. | Microsoft Docs"
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
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator ohne As-Klausel; Typ &quot;Object&quot; wird angenommen.
Eine Operatorprozedur gibt keine `As`\-Klausel an.  
  
 Eine `As`\-Klausel bezeichnet einen Datentyp, der einem Programmierelement zugeordnet werden soll. In einer [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) gibt sie den Datentyp des Werts an, den die Operatorprozedur an den aufrufenden Code zurückgibt. Wenn Sie keine `As`\-Klausel in die `Operator`\-Anweisung einfügen, lautet der Rückgabedatentyp standardmäßig `Object`.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC41005  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie eine `As`\-Klausel in die `Operator`\-Anweisung ein, um den Rückgabedatentyp anzugeben.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)