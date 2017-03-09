---
title: "Der Name des Felds oder der Eigenschaft, das bzw. die initialisiert wird, muss mit einem Punkt (.) beginnen. | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Name des Felds oder der Eigenschaft, das bzw. die initialisiert wird, muss mit einem Punkt (.) beginnen.
Jedem Memberinitialisierer in einer Objektinitialisierungsliste gibt den Namen eines Felds oder einer Eigenschaft sowie den ursprünglichen Wert an. Dem Namen des Felds oder der Eigenschaft muss ein Punkt vorangestellt sein. Die folgende Deklaration weist der `Name`\-Eigenschaft von `client` beispielsweise „Microsoft“ als Anfangswert zu.  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **Fehler\-ID:** BC30985  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie jedem Membernamen einen Punkt voraus.  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Eigenschaftenprozeduren oder Felder](http://msdn.microsoft.com/de-de/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)