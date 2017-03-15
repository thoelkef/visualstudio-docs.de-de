---
title: "Funktion ohne As-Klausel. R&#252;ckgabetyp &#39;Object&#39; wird angenommen. | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Funktion ohne As-Klausel. R&#252;ckgabetyp &#39;Object&#39; wird angenommen.
Eine `Function`\-Prozedur gibt keine `As`\-Klausel an.  
  
 Eine `As`\-Klausel bezeichnet einen Datentyp, der einem Programmierelement zugeordnet werden soll. In einer [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) gibt sie den Datentyp des Werts an, den die `Function`\-Prozedur an den aufrufenden Code zurückgibt. Wenn Sie keine `As`\-Klausel in die `Function`\-Anweisung einfügen, lautet der Rückgabedatentyp standardmäßig `Object`.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42021  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie eine `As`\-Klausel in die `Function`\-Anweisung ein, um den Rückgabedatentyp anzugeben.  
  
## Siehe auch  
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)