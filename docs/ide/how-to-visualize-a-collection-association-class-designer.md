---
title: "How to: Visualize a Collection Association (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.collectionassociationline"
  - "vs.classdesigner.ShowAssociationException"
helpviewer_keywords: 
  - "collection associations"
  - "collections, collection associations"
  - "Class Designer [Visual Studio], collection associations"
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Visualize a Collection Association (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eigenschaften und Felder, die Auflistungen anderer Typen sind, können im Klassendiagramm als Auflistungsassoziation angezeigt werden.  Im Gegensatz zu einer Standardassoziation, bei der ein Feld oder eine Eigenschaft als Linie zwischen der übergeordneten Klasse und dem Typ des Felds angezeigt wird, wird eine Auflistungsassoziation als Linie zwischen der übergeordneten Klasse und dem aufgelisteten Typ angezeigt.  
  
### So erstellen Sie eine Auflistungsassoziation  
  
1.  Erstellen Sie im Code eine Eigenschaft oder ein Feld, deren bzw. dessen Typ eine Auflistung mit starker Typbindung ist.  
  
2.  Erweitern Sie im Klassendiagramm die Klasse, damit Eigenschaften und Felder angezeigt werden.  
  
3.  Klicken Sie in der Klasse mit der rechten Maustaste auf das Feld oder die Eigenschaft, und wählen Sie **Als Auflistungsassoziation anzeigen** aus.  
  
     Die Eigenschaft oder das Feld wird als Assoziationslinie zum aufgelisteten Typ angezeigt.  
  
## Siehe auch  
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)