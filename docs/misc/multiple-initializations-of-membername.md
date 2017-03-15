---
title: "Mehrfache Initialisierungen von &quot;&lt;Membername&gt;&quot; | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mehrfache Initialisierungen von &quot;&lt;Membername&gt;&quot;
Mehrfache Initialisierungen von "\<Membername\>". Felder und Eigenschaften können in einem Objektinitialisiererausdruck nur einmal initialisiert werden.  
  
 Sie können jedem Feld und jeder Eigenschaft in einer Objektinitialisierungsliste nur einmal einen Anfangswert zuweisen. Die folgende Deklaration ist ungültig.  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  Sie können ein Feld oder eine Eigenschaft als Anfangswert für einen anderen Member verwenden, wie in der folgenden Deklaration gezeigt.  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **Fehler\-ID:** BC30989  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie für jedes Feld oder jede Eigenschaft in der Objektinitialisiererliste alle Initialisierungen bis auf eine.  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Eigenschaftenprozeduren oder Felder](http://msdn.microsoft.com/de-de/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)