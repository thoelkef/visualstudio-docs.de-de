---
title: "Die New-Einschr&#228;nkung und die Structure-Einschr&#228;nkung k&#246;nnen nicht kombiniert werden. | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die New-Einschr&#228;nkung und die Structure-Einschr&#228;nkung k&#246;nnen nicht kombiniert werden.
Eine Einschränkungsliste enthält sowohl die [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)\-Einschränkung als auch die [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\-Einschränkung.  
  
 Eine Einschränkungsliste für einen Typparameter kann angeben, dass das an den Typparameter übergebene Argument ein Werttyp \(mit der `Structure`\-Einschränkung\) oder ein Referenztyp sein muss \(mit der [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\-Einschränkung\). Sie dürfen nicht beide Einschränkungen für den gleichen Typparameter angeben, und Sie dürfen keine dieser Einschränkungen mehrmals angeben.  
  
 Die `New`\-Einschränkung gibt an, dass das Typargument einen parameterlosen Konstruktor verfügbar machen muss, auf den der erstellende Code zugreifen kann. Eine Struktur kann aber keinen nicht freigegebenen parameterlosen Konstruktor haben. Aus diesem Grund verursachen die Einschränkungen `New` und `Structure` einen Konflikt.  
  
 **Fehler\-ID:** BC32103  
  
### So beheben Sie diesen Fehler  
  
1.  Entscheiden Sie, ob für das Typargument ein Werttyp oder ein Verweistyp erforderlich sein soll.  
  
2.  Soll das Typargument ein Werttyp sein, entfernen Sie das `New`\-Schlüsselwort aus der Einschränkungsliste.  
  
3.  Soll das Typargument ein Verweistyp sein, entfernen Sie das `Structure`\-Schlüsselwort aus der Einschränkungsliste.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)