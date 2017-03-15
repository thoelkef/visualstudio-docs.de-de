---
title: "Der Member &quot;&lt;Membername&gt;&quot; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da er freigegeben ist. | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Member &quot;&lt;Membername&gt;&quot; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da er freigegeben ist.
Objektinitialisierer können nicht verwendet werden, um einen beliebigen Member einer Klasse zu initialisieren, der freigegeben ist. Weitere Informationen finden Sie unter [Shared](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 **Fehler\-ID:** BC30991  
  
### So beheben Sie diesen Fehler  
  
1.  Untersuchen Sie die Klassendefinition, um zu bestimmen, welches Element als "shared" deklariert ist.  
  
2.  Entfernen Sie die Initialisierung für das Element aus der Objektinitialisiererliste.  
  
## Beispiel  
 Im folgenden Beispiel ist `totalCustomers` ein freigegebener Member.  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 Da `totalCustomers` freigegeben ist, wird beim Versuch, den Anfangswert in einer Objektinitialisiererliste festzulegen, dieser Fehler verursacht.  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NICHT IM BUILD: Freigegebene Member in Visual Basic](http://msdn.microsoft.com/de-de/dbc3783f-83a2-4225-995d-c2d6d025663d)