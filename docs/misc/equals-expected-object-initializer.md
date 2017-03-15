---
title: "&quot;=&quot; erwartet (Objektinitialisierer). | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;=&quot; erwartet (Objektinitialisierer).
Um den Anfangswert für ein Feld oder eine Eigenschaft in der Deklaration eines Objektinitialisierers einzurichten, müssen Sie ein Gleichheitszeichen verwenden. Die folgende Deklaration weist der `Name`\-Eigenschaft von `client` beispielsweise "Microsoft" als Anfangswert zu.  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **Fehler\-ID:** BC30984  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie ein Gleichheitszeichen an der im vorherigen Beispiel dargestellten Position hinzu.  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NICHT IM BUILD: Eigenschaftenprozeduren oder Felder](http://msdn.microsoft.com/de-de/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)