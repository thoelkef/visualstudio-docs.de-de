---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Klassen\-Designer können Sie eine Schnittstelle im Klassendiagramm implementieren. Dazu erstellen eine Verbindung zu einer Klasse, in der Code für die Schnittstellenmethoden enthalten ist.  Der Klassen\-Designer generiert eine Schnittstellenimplementierung und stellt die Beziehung zwischen der Schnittstelle und der Klasse als Vererbungsbeziehung dar.  Um eine Schnittstelle zu implementieren, zeichnen Sie eine Vererbungslinie von der Schnittstelle zu der Klasse oder ziehen die Schnittstelle aus der Klassenansicht.  
  
> [!TIP]
>  Schnittstellen werden genauso erstellt wie andere Typen.  Falls die Schnittstelle vorhanden ist, aber im Klassendiagramm nicht angezeigt wird, zeigen Sie sie zunächst an.  Weitere Informationen finden Sie unter [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) und [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md).  
  
### So implementieren Sie eine Schnittstelle durch Zeichnen einer Vererbungslinie  
  
1.  Zeigen Sie im Klassendiagramm die Schnittstelle und die Klasse für die Schnittstellenimplementierung an.  
  
2.  Zeichnen Sie eine Vererbungslinie von der Klasse zur Schnittstelle.  
  
     An die Klasse wird ein Lollipop angehängt, und eine Beschriftung mit dem Schnittstellennamen zeigt die Vererbungsbeziehung an.  Visual Studio generiert Stubs für alle Schnittstellenmember.  
  
 Weitere Informationen finden Sie unter [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### So implementieren Sie eine Schnittstelle in der Klassenansicht  
  
1.  Zeigen Sie im Klassendiagramm die Klasse an, die die Schnittstelle implementieren soll.  
  
2.  Öffnen Sie die Klassenansicht, und suchen Sie nach der Schnittstelle.  
  
    > [!TIP]
    >  Wenn die Klassenansicht nicht geöffnet ist, rufen Sie sie im Menü **Ansicht** auf.  Weitere Informationen über die Klassenansicht finden Sie unter [Viewing Classes and Their Members](http://msdn.microsoft.com/de-de/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Ziehen Sie den Schnittstellenknoten auf die Klassenform im Diagramm.  
  
     An die Klasse wird ein Lollipop angehängt, und eine Beschriftung mit dem Schnittstellennamen zeigt die Vererbungsbeziehung an.  Visual Studio generiert Stubs für alle Schnittstellenmember. Die Schnittstelle wurde nun implementiert.  
  
## Siehe auch  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)