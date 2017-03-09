---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; wurde nicht als &#39;Public&#39; deklariert und kann daher nicht auf &#39;&lt;Klassenname&gt;&#39; angewendet werden. | Microsoft Docs"
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
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; wurde nicht als &#39;Public&#39; deklariert und kann daher nicht auf &#39;&lt;Klassenname&gt;&#39; angewendet werden.
Eine Klasse ist mit <xref:Microsoft.VisualBasic.ComClassAttribute> deklariert, aber in ihrer Deklaration wird `Public` nicht angegeben.  
  
 Die Eignung einer .NET Framework\-Klasse für COM\-Interop setzt die Erfüllung der folgenden Anforderungen voraus:  
  
-   Sie muss `Public` sein, alle ihre Container müssen `Public` sein, und sie muss mindestens einen `Public`\-Member verfügbar machen.  
  
-   Sie darf nicht *abstrakt* sein. Sie darf also nicht mit `MustInherit` deklariert werden.  
  
-   Sie darf nicht generisch sein oder in einem generischen Containertyp deklariert werden.  
  
 **Fehler\-ID:** BC32509  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie der Klassendeklaration das Schlüsselwort `Public` hinzu.  
  
     \- oder \-  
  
-   Wenn die Klasse oder ihr enthaltendes Element nicht `Public` sein darf, entfernen Sie <xref:Microsoft.VisualBasic.ComClassAttribute> aus der Klassendeklaration. Sie können sie nicht für COM verfügbar machen.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)