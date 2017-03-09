---
title: "&quot;&lt;derivedtypename&gt;&quot; erweitert den Zugriff des &quot;&lt;internaltypename&gt;&quot;-Typs au&#223;erhalb der Assembly und kann daher nicht vom  &quot;&lt;constructedbasetypename&gt;&quot;-&lt;type&gt; erben. | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;derivedtypename&gt;&quot; erweitert den Zugriff des &quot;&lt;internaltypename&gt;&quot;-Typs au&#223;erhalb der Assembly und kann daher nicht vom  &quot;&lt;constructedbasetypename&gt;&quot;-&lt;type&gt; erben.
Eine abgeleitete Klasse oder Schnittstelle versucht, die Zugriffsebene eines eingeschränkten Typs zu erweitern, indem sie diesen als Typargument für eine Basisklasse oder Schnittstelle verwendet.  
  
 Dieser Fehler kann durch folgenden Code generiert werden.  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 Code außerhalb der Assembly darf nicht auf die `restrictedStructure` zugreifen. Allerdings kann jeder Code auf die `derivedClass` zugreifen, der darauf verweisen kann. Daher kann die `derivedClass` die `baseClass` nicht erben, wenn sie die `restrictedStructure` als Typargument verwendet, da auf diese Weise die `restrictedStructure` für Code in jeder beliebigen Assembly verfügbar gemacht würde.  
  
 **Fehler\-ID:** BC30922  
  
### So beheben Sie diesen Fehler  
  
-   Passen Sie die Zugriffsebenen der Klassen oder Schnittstellen so an, dass der abgeleitete Typ die Zugriffsebene des eingeschränkten Typs nicht erweitert.  
  
     \- oder \-  
  
-   Wenn Sie die Zugriffsebenen nicht anpassen können, verwenden Sie beim Erstellen der Basisklasse oder Schnittstelle den eingeschränkten Typ nicht als Typargument.  
  
## Siehe auch  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)