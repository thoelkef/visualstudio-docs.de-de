---
title: "Die Structure-Einschr&#228;nkung kann nicht mehrmals f&#252;r den gleichen Typparameter angegeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32102"
  - "vbc32102"
helpviewer_keywords: 
  - "BC32102"
ms.assetid: f4ebd416-7fb9-4a24-a8df-e9ee7ccc2c76
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Structure-Einschr&#228;nkung kann nicht mehrmals f&#252;r den gleichen Typparameter angegeben werden.
Eine Einschränkungsliste enthält die [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\-Einschränkung mehrfach.  
  
 Eine Einschränkungsliste für einen Typparameter kann angeben, dass das an den Typparameter übergebene Argument ein Werttyp \(mit der `Structure`\-Einschränkung\) oder ein Verweistyp sein muss \(mit der [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\-Einschränkung\). Sie dürfen nicht beide Einschränkungen für den gleichen Typparameter angeben, und Sie dürfen keine dieser Einschränkungen mehrmals angeben.  
  
 Fehler\-ID: BC32102  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie alle redundanten `Structure`\-Schlüsselwörter. In der Einschränkungsliste sollte nur ein Vorkommen enthalten sein.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)