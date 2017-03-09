---
title: "&#39;&lt;typname&gt;&#39; ist ein generischer Typ, der Typargumente erfordert. | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typname&gt;&#39; ist ein generischer Typ, der Typargumente erfordert.
Für eine Variable, einen Prozedurparameter oder einen Funktionsrückgabewert ist in der Deklaration die Angabe eines generischen Klassen\- oder Strukturtyps festgelegt, die Deklaration enthält aber keine Typargumente.  
  
 Naturgemäß ist jede generische Klasse und Struktur mit mindestens einem Typparameter definiert. Wenn Sie einen generischen Typ für die Deklaration einer konstruierten Klasse oder Struktur verwenden, müssen Sie für jeden vom generischen Typ definierten Typparameter ein Typargument angeben.  
  
 **Fehler\-ID:** BC32076  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie der Deklaration eine Typliste hinzu, in Klammern eingeschlossen und mit dem Schlüsselwort `Of` beginnend.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)