---
title: "Die Class-Einschr&#228;nkung und die Structure-Einschr&#228;nkung k&#246;nnen nicht kombiniert werden. | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Class-Einschr&#228;nkung und die Structure-Einschr&#228;nkung k&#246;nnen nicht kombiniert werden.
Eine Einschränkungsliste enthält sowohl die [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\-Einschränkung als auch die [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\-Einschränkung.  
  
 Eine Einschränkungsliste für einen Typparameter kann angeben, dass das an den Typparameter übergebene Argument ein Werttyp \(mit der `Structure`\-Einschränkung\) oder ein Verweistyp sein muss \(mit der `Class`\-Einschränkung\). Sie dürfen nicht beide Einschränkungen für den gleichen Typparameter angeben, und Sie dürfen keine dieser Einschränkungen mehrmals angeben.  
  
 **Fehler\-ID:** BC32104  
  
### So beheben Sie diesen Fehler  
  
1.  Entscheiden Sie, ob für das Typargument ein Werttyp oder ein Verweistyp erforderlich sein soll.  
  
    -   Soll das Typargument ein Werttyp sein, entfernen Sie das `Class`\-Schlüsselwort aus der Einschränkungsliste.  
  
    -   Soll das Typargument ein Verweistyp sein, entfernen Sie das `Structure`\-Schlüsselwort aus der Einschränkungsliste.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)