---
title: "Die Membereigenschaft &#39;&lt;propertyname&gt;&#39; eines anonymen Typs kann nicht zum Ableiten des Typs einer anderen Membereigenschaft verwendet werden, da der Typ von &#39;&lt;propertyname&gt;&#39; noch nicht bekannt ist. | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Membereigenschaft &#39;&lt;propertyname&gt;&#39; eines anonymen Typs kann nicht zum Ableiten des Typs einer anderen Membereigenschaft verwendet werden, da der Typ von &#39;&lt;propertyname&gt;&#39; noch nicht bekannt ist.
Erst ab dem Zeitpunkt, da der Typ der Eigenschaft eines anonymen Typs bekannt ist, kann sie zum Festlegen des Typs einer anderen Eigenschaft verwendet werden. Beispielsweise ist in der folgenden Deklaration `.IDName = .LastName` ungültig, da `.LastName` noch nicht initialisiert wurde.  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **Fehler\-ID:** BC36559  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie den Typ der Eigenschaft fest, bevor Sie sie verwenden, um eine andere Eigenschaft zu initialisieren.  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## Siehe auch  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Gewusst wie: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)