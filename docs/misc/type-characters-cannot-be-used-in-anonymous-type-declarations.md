---
title: "Typzeichen k&#246;nnen in anonymen Typdeklarationen nicht verwendet werden | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typzeichen k&#246;nnen in anonymen Typdeklarationen nicht verwendet werden
Sie können kein Typzeichen für einen Eigenschaftennamen verwenden, wenn Sie eine Instanz eines anonymen Typs deklarieren. Der Datentyp der Eigenschaft wird vom zugewiesenen Wert abgeleitet. Beispielsweise sind die folgenden Deklarationen ungültig.  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **Fehler\-ID:** BC36560  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Typzeichen aus der Initialisiererliste. Sie können den zugewiesenen Wert ggf. explizit konvertieren, um den für die Eigenschaft gewünschten Datentyp festzulegen.  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## Siehe auch  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Gewusst wie: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)