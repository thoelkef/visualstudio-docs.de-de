---
title: "Der Member &quot;&lt;Membername&gt;&quot; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da er kein Feld und keine Eigenschaft ist | Microsoft Docs"
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
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Member &quot;&lt;Membername&gt;&quot; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da er kein Feld und keine Eigenschaft ist
Eine Objektinitialisiererliste kann keine freigegebenen Member, Konstanten oder Methodenaufrufe enthalten. Die in der Initialisiererliste enthaltenen Member müssen Felder oder Eigenschaften sein, und Eigenschaftenmember können keine Argumente erfordern.  
  
 **Fehler\-ID:** BC30990  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie alle freigegebenen Member, Konstanten, Methodenaufrufe oder Eigenschaften, die über Parameter verfügen, aus der Objektinitialisiererliste.  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Freigegebene Member in Visual Basic](http://msdn.microsoft.com/de-de/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NICHT IM BUILD: Standardeigenschaften](http://msdn.microsoft.com/de-de/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NotInBuild: Objektmember](http://msdn.microsoft.com/de-de/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)