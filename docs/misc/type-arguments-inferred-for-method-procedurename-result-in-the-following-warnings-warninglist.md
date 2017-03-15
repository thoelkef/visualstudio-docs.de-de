---
title: "Die Typargumente, die per R&#252;ckschluss f&#252;r die &quot;&lt;Prozedurname&gt;&quot;-Methode abgeleitet wurden, verursachen die folgenden Warnungen: &lt;Warnungsliste&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Typargumente, die per R&#252;ckschluss f&#252;r die &quot;&lt;Prozedurname&gt;&quot;-Methode abgeleitet wurden, verursachen die folgenden Warnungen: &lt;Warnungsliste&gt;
Eine generische Prozedur wurde ohne Angabe von Typargumenten aufgerufen, und die abgeleiteten Typargumente führen zu einer oder mehreren Warnungen.  
  
 Wenn Sie einen generischen Typ aufrufen, geben Sie in der Regel für jeden Typparameter, der durch den generischen Typ definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn die abgeleiteten Typen Mehrdeutigkeiten verursachen oder eine Situation hervorrufen, die zu unerwarteten Ergebnissen führen kann, generiert der Compiler diese Warnung.  
  
 Eine *Einschränkung* für einen Typparameter schränkt die Typargumente ein, die an den Typparameter übergeben werden können. Ein Typparameter kann z. B. auf eine Klasse eingeschränkt werden, die die <xref:System.IComparable%601>\-Schnittstelle implementiert. Weitere Informationen finden Sie in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures) unter "Einschränkungen".  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC41006  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie Typargumente für die generische Prozedur an, damit der Compiler sie nicht ableiten muss.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)