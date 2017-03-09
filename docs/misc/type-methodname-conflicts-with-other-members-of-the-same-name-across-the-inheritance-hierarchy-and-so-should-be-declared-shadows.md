---
title: "&lt;Typ&gt; &#39;&lt;Methodenname&gt;&#39; steht mit anderen Membern desselben Namens in der Vererbungshierarchie in Konflikt und sollte daher als „Shadows“ deklariert werden. | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Typ&gt; &#39;&lt;Methodenname&gt;&#39; steht mit anderen Membern desselben Namens in der Vererbungshierarchie in Konflikt und sollte daher als „Shadows“ deklariert werden.
Eine Schnittstelle, die von zwei oder mehr Schnittstellen erbt, definiert eine Prozedur mit demselben Namen wie für eine Prozedur, die bereits in mehr als einer der Basisschnittstellen definiert ist. Die Prozedur in dieser Schnittstelle muss eine der Prozeduren der Basisschnittstelle überschatten.  
  
 Diese Meldung ist eine Warnung.`Shadows` wird standardmäßig angenommen. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42000  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie eine der Prozeduren der Basisschnittstelle ausblenden möchten, fügen Sie das `Shadows`\-Schlüsselwort zur neuen Prozedurdeklaration hinzu.  
  
-   Wenn Sie keine der Prozeduren der Basisschnittstelle ausblenden möchten, ändern Sie den Namen der neuen Prozedur.  
  
## Siehe auch  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)