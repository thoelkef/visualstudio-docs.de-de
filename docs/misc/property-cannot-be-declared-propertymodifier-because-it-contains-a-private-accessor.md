---
title: "Die Eigenschaft kann nicht als &quot;&lt;Eigenschaftenmodifizierer&gt;&quot; deklariert werden, da sie einen &quot;Private&quot;-Accessor enth&#228;lt | Microsoft Docs"
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
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Eigenschaft kann nicht als &quot;&lt;Eigenschaftenmodifizierer&gt;&quot; deklariert werden, da sie einen &quot;Private&quot;-Accessor enth&#228;lt
Eine Eigenschaft mit einer `Private`\-Eigenschaftenprozedur \(`Get` oder `Set`\) wird als [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable) gekennzeichnet.  
  
 Ist eine Eigenschaft oder Prozedur einer Basisklasse als [Private](/dotnet/visual-basic/language-reference/modifiers/private) deklariert, kann diese Eigenschaft oder Prozedur nicht von einer abgeleiteten Klasse überschrieben werden, da diese nicht auf die Eigenschaft oder Prozedur zugreifen kann. Daher können Sie `Private` nicht in Verbindung mit `Overridable` verwenden. Dies gilt nicht nur für die Eigenschaft selbst, sondern auch für die einzelnen Eigenschaftenprozeduren.  
  
 **Fehler\-ID:** BC31108  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Overridable`\-Schlüsselwort aus der [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), oder entfernen Sie das `Private`\-Schlüsselwort aus der [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) oder der [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)