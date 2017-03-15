---
title: "Typzeichen k&#246;nnen nicht in einer Typparameterdeklaration verwendet werden. | Microsoft Docs"
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
  - "vbc32041"
  - "bc32041"
helpviewer_keywords: 
  - "BC32041"
ms.assetid: 24f9a514-f3d4-46c3-805c-71225f6fec59
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typzeichen k&#246;nnen nicht in einer Typparameterdeklaration verwendet werden.
Eine Typparameterdeklaration enthält mindestens ein Typkennzeichen.  
  
 Ein Typparameter eines generischen Typs muss ein gültiger Visual Basic\-Name sein. Die Typkennzeichen \(`%`, `&`, `@`, `!`, `#` und `$`\) sind keine zulässigen Zeichen. Siehe [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 **Fehler\-ID:** BC32041  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Typkennzeichen aus der Typparameterdeklaration.  
  
## Siehe auch  
 [Type Characters](/dotnet/visual-basic/programming-guide/language-features/data-types/type-characters)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)