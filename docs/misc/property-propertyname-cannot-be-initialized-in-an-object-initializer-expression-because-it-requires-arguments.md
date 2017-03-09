---
title: "Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da sie Argumente erfordert. | Microsoft Docs"
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
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da sie Argumente erfordert.
Die in einer Objektinitialisiererliste initialisierten Member müssen Felder oder Eigenschaften sein, und Eigenschaftenmember können keine Parameter haben. Standardeigenschaften erfordern beispielsweise Argumente, daher können sie nicht in einer Objektinitialisiererliste initialisiert werden. Weitere Informationen finden Sie unter [NICHT IM BUILD: Standardeigenschaften](http://msdn.microsoft.com/de-de/a70f2a27-8176-4858-935e-f25afdd43ab5).  
  
 **Fehler\-ID:** BC30992  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie aus der Initialisierungsliste alle Eigenschaften, die Argumente haben.  
  
## Beispiel  
 Die folgende Klasse enthält eine Standardeigenschaft `defaultProp`, die ein ganzzahliges Argument erfordert.  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 Da die Standardeigenschaft ein Argument erfordert, verursacht die folgende Deklaration einen Fehler.  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## Siehe auch  
 [NICHT IM BUILD: Standardeigenschaften](http://msdn.microsoft.com/de-de/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)