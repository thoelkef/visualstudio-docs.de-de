---
title: "Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da alle &#220;berladungen, auf die zugegriffen werden kann, Argumente erfordern. | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht in einem Objektinitialisiererausdruck initialisiert werden, da alle &#220;berladungen, auf die zugegriffen werden kann, Argumente erfordern.
Die in einer Objektinitialisiererliste initialisierten Member müssen Felder oder Eigenschaften sein. Außerdem können Eigenschaften in einer Initialisiererliste keine Parameter haben. Die Eigenschaft, die diesen Fehler verursacht, ist überladen, und jede ihrer Versionen erfordert Argumente. Aus diesem Grund kann die Eigenschaft in einer Objektinitialisiererliste nicht initialisiert werden.  
  
 **Fehler\-ID:** BC30993  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Eigenschaft, für die Argumente erforderlich sind, aus der Initialisiererliste.  
  
## Beispiel  
 Die folgende Klasse enthält drei Eigenschaftendefinitionen: eine für `TotalItems` und zwei für `Item`. Letztere ist überladen.  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 Die `TotalItems`\-Eigenschaft erfordert keine Argumente und kann in einer Objektinitialisiererliste initialisiert werden, wie in der folgenden Deklaration dargestellt.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 Die `Item`\-Eigenschaft ist überladen, und jede Überladung erfordert ein Argument. Aus diesem Grund darf `Item` nicht in einer Objektinitialisiererliste enthalten sein.  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 Um diesen Fehler zu vermeiden, initialisieren Sie die `Item`\-Eigenschaft außerhalb des Objektinitialisierers.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## Siehe auch  
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Standardeigenschaften](http://msdn.microsoft.com/de-de/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)