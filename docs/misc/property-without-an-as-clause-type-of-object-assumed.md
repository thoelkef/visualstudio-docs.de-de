---
title: "Eigenschaft ohne As-Klausel; Typ &quot;Object&quot; wird angenommen | Microsoft Docs"
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
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eigenschaft ohne As-Klausel; Typ &quot;Object&quot; wird angenommen
In einer Eigenschaftendeklaration wird keine `As`\-Klausel angegeben.  
  
 Eine `As`\-Klausel bezeichnet einen Datentyp, der einem Programmierelement zugeordnet werden soll. In einer [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) gibt sie den Datentyp des Werts an, den die `Get`\-Prozedur der Eigenschaft an den aufrufenden Code zurückgibt. Wenn Sie keine `As`\-Klausel in die `Property`\-Anweisung einfügen, lautet der Datentyp der Eigenschaft standardmäßig `Object`.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42022  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie eine `As`\-Klausel in die `Property`\-Anweisung ein, um den Datentyp der Eigenschaft anzugeben.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)