---
title: "CA1040: Leere Schnittstellen vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1040"
  - "AvoidEmptyInterfaces"
helpviewer_keywords: 
  - "AvoidEmptyInterfaces"
  - "CA1040"
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1040: Leere Schnittstellen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Von der Schnittstelle werden keine Member deklariert oder mindestens zwei weitere Schnittstellen implementiert.  
  
## Regelbeschreibung  
 Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen.  Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht.  Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt.  Eine leere Schnittstelle definiert keine Member.  Daher definiert sie keinen Vertrag, der implementiert werden kann.  
  
 Wenn Ihr Design leere Schnittstellen umfasst, die von Typen implementiert werden sollen, wird eine Schnittstelle wahrscheinlich als Marker oder zur Identifizierung einer Gruppe von Typen verwendet.  Wenn diese Identifizierung zur Laufzeit stattfindet, müssen Sie zur richtigen Durchführung dieses Vorgangs ein benutzerdefiniertes Attribut verwenden.  Überprüfen Sie, ob das Attribut bzw. dessen Eigenschaften vorhanden sind oder fehlen, um die Zieltypen zu identifizieren.  Wenn die Identifikation zur Kompilierungszeit erfolgen muss, ist die Verwendung einer leeren Schnittstelle zulässig.  
  
## Behandeln von Verstößen  
 Entfernen Sie die Schnittstelle, oder fügen Sie der Schnittstelle Member hinzu.  Wenn die leere Schnittstelle zur Bezeichnung einer Reihe von Typen verwendet wird, ersetzen Sie die Schnittstelle durch ein benutzerdefiniertes Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Schnittstelle zur Kompilierungszeit dazu verwendet wird, eine Reihe von Typen zu identifizieren.  
  
## Beispiel  
 Im folgenden Beispiel wird eine leere Schnittstelle veranschaulicht.  
  
 [!code-cs[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]