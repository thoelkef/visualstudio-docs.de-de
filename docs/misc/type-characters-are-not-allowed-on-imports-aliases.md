---
title: "Typzeichen sind in Imports-Aliasen nicht zul&#228;ssig | Microsoft Docs"
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
  - "vbc31398"
  - "BC31398"
helpviewer_keywords: 
  - "BC31398"
ms.assetid: 0620669d-b529-49f3-9deb-aeda4dacc58a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typzeichen sind in Imports-Aliasen nicht zul&#228;ssig
Ein Importalias in einer `Imports`\-Anweisung enthält mindestens ein Typkennzeichen.  
  
 Ein Importalias muss ein gültiger Visual Basic\-Name sein. Die Typkennzeichen \(`%`, `&`, `@`, `!`, `#` und `$`\) sind keine zulässigen Zeichen. Siehe [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 **Fehler\-ID:** BC31398  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Typkennzeichen aus dem Importalias.  
  
## Siehe auch  
 [Type Characters](/dotnet/visual-basic/programming-guide/language-features/data-types/type-characters)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)