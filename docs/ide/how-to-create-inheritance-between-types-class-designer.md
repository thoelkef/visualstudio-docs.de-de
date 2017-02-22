---
title: "How to: Create Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritanceline"
helpviewer_keywords: 
  - "inheritance, relationship defining"
  - "relationships, defining inheritance"
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
caps.handback.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um eine Vererbungsbeziehung zwischen zwei Typen in einem Klassendiagramm mithilfe des Klassen\-Designers zu erstellen, verbinden Sie den Basistyp mit seinem abgeleiteten Typ bzw. seinen abgeleiteten Typen.  Eine Vererbungsbeziehung kann zwischen zwei Klassen, zwischen einer Klasse und einer Schnittstelle oder zwischen zwei Schnittstellen hergestellt werden.  
  
### So erstellen Sie eine Vererbung zwischen Typen  
  
1.  Öffnen Sie vom Projekt im Projektmappen\-Explorer aus eine Klassendiagrammdatei \(CD\-Datei\).  
  
     Wenn Sie noch nicht über ein Klassendiagramm verfügen, erstellen Sie eines.  Siehe [How to: Add Class Diagrams to Projects \(Class Designer\)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  Klicken Sie im **Werkzeugkasten** unter **Klassen\-Designer** auf **Vererbung**.  
  
3.  Zeichnen Sie im Klassendiagramm eine Vererbungslinie zwischen den gewünschten Typen. Beginnen Sie folgendermaßen:  
  
    -   Von einer abgeleiteten Klasse zur Basisklasse  
  
    -   Von einer implementierenden Klasse zur implementierten Schnittstelle  
  
    -   Von einer erweiternden Schnittstelle zu einer erweiterten Schnittstelle  
  
4.  Wenn Sie über einen abgeleiteten Typ eines generischen Typs verfügen, können Sie optional auf die Vererbungslinie klicken.  Legen Sie im Fenster **Eigenschaften** die **Type Arguments**\-Eigenschaft so fest, dass sie mit dem Typ übereinstimmt, den der generische Typ aufweisen soll.  
  
    > [!NOTE]
    >  Wenn eine übergeordnete abstrakte Klasse mindestens einen abstrakten Member enthält, so werden alle abstrakten Member als nicht abstrakte vererbende Klassen implementiert.  Siehe [Implementing Abstract Base Classes](../ide/refactoring-classes-and-types-class-designer.md#ImplementingAbstractBaseClasses).  
    >   
    >  Sie können vorhandene generische Typen zwar visualisieren, Sie können jedoch keine neuen generischen Typen erstellen.  Es ist auch nicht möglich, die Typparameter für vorhandene generische Typen zu ändern.  
  
## Siehe auch  
 [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)