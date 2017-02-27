---
title: "How to: Change Between Member Notation and Association Notation (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "notation, member"
  - "association notation"
  - "member notation"
  - "notation, association"
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Change Between Member Notation and Association Notation (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Klassen\-Designer können Sie die Anzeige eines Assoziationsverhältnisses zwischen zwei Typen im Klassendiagramm von der Membernotation in die Assoziationsnotation und umgekehrt ändern.  Anhand der als Assoziationslinien angezeigten Member wird deutlich, wie Typen miteinander in Beziehung stehen.  
  
> [!NOTE]
>  Assoziationsverhältnisse können als Membereigenschaft oder \-feld dargestellt werden.  Um die Membernotation in die Assoziationsnotation zu ändern, muss ein Typ über einen Member eines anderen Typs verfügen.  Um die Assoziationsnotation in die Membernotation zu ändern, müssen beide Typen über eine Assoziationslinie miteinander verbunden sein.  Weitere Informationen finden Sie unter [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md).  Wenn das Projekt mehrere Klassendiagramme enthält, wirkt sich die Änderung der Anzeige von Assoziationsverhältnissen im Diagramm nur auf das Diagramm selbst aus.  Um die Anzeige von Assoziationsverhältnissen in einem anderen Diagramm zu ändern, öffnen Sie das entsprechende Diagramm und führen die beschriebenen Schritte aus.  
  
### So ändern Sie die Membernotation in die Assoziationsnotation  
  
1.  Öffnen Sie vom Projektknoten im Projektmappen\-Explorer aus die Klassendiagrammdatei \(CD\-Datei\).  
  
2.  Klicken Sie in der Typform im Klassendiagramm mit der rechten Maustaste auf die Membereigenschaft bzw. das Memberfeld, die bzw. das die Assoziation darstellt, und wählen Sie **Als Assoziation anzeigen** aus.  
  
    > [!TIP]
    >  Falls in der Typform keine Eigenschaften oder Felder angezeigt werden, wurden möglicherweise die Depots in der Form reduziert.  Um die Typform zu erweitern, doppelklicken Sie auf den Depotnamen, oder klicken Sie mit der rechten Maustaste auf die Typform und wählen **Erweitern** aus.  
  
     Der Member wird im Depot in der Typform nicht mehr angezeigt, und es wird eine Assoziationslinie zwischen den beiden Typen angezeigt.  Die Assoziationslinie wird mit dem Namen der Eigenschaft oder des Felds gekennzeichnet.  
  
### So ändern Sie die Assoziationsnotation in die Membernotation  
  
-   Klicken Sie im Klassendiagramm mit der rechten Maustaste auf die Assoziationslinie, und wählen Sie je nach Bedarf **Als Eigenschaft anzeigen** oder **Als Feld anzeigen** aus.  
  
     Die Assoziationslinie wird entfernt, und die Eigenschaft wird im entsprechenden Depot in der Typform im Diagramm angezeigt.  
  
## Siehe auch  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)   
 [How to: Visualize a Collection Association \(Class Designer\)](../ide/how-to-visualize-a-collection-association-class-designer.md)