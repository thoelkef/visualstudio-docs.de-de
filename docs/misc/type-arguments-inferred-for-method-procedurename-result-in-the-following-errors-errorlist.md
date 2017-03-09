---
title: "Die Typargumente, die per R&#252;ckschluss f&#252;r die &quot;&lt;Prozedurname&gt;&quot;-Methode abgeleitet wurden, verursachen die folgenden Fehler: &lt;Fehlerliste&gt; | Microsoft Docs"
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
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Typargumente, die per R&#252;ckschluss f&#252;r die &quot;&lt;Prozedurname&gt;&quot;-Methode abgeleitet wurden, verursachen die folgenden Fehler: &lt;Fehlerliste&gt;
Eine generische Prozedur wurde ohne Angabe von Typargumenten aufgerufen, und die abgeleiteten Typargumente führen zu einer oder mehreren Einschränkungsverletzungen.  
  
 Wenn Sie einen generischen Typ aufrufen, geben Sie in der Regel für jeden Typparameter, der durch den generischen Typ definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn die abgeleiteten Typen eine oder mehrere der Einschränkungen für Typparameter nicht erfüllen, generiert der Compiler diesen Fehler.  
  
 Eine *Einschränkung* für einen Typparameter schränkt die Typargumente ein, die an den Typparameter übergeben werden können. Ein Typparameter kann z. B. auf eine Klasse eingeschränkt werden, die die <xref:System.IComparable%601>\-Schnittstelle implementiert. Weitere Informationen finden Sie in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures) unter "Einschränkungen".  
  
 **Fehler\-ID:** BC30954  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie Typargumente für die generische Prozedur an, damit der Compiler sie nicht ableiten muss.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)