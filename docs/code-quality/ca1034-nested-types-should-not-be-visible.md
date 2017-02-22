---
title: "CA1034: Geschachtelte Typen sollten nicht sichtbar sein | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1034: Geschachtelte Typen sollten nicht sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Extern sichtbare Typen enthalten extern sichtbare Typdeklarationen.  Geschachtelte Enumerationen und geschützte Typen sind von dieser Regel befreit.  
  
## Regelbeschreibung  
 Ein geschachtelter Typ ist ein Typ, der innerhalb des Gültigkeitsbereichs eines anderen Typs deklariert ist.  Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails der enthaltenden Typen.  Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein.  
  
 Extern sichtbare geschachtelte Typen dürfen nicht für logische Gruppierungen oder zur Vermeidung von Namenskonflikten verwendet werden. Stattdessen sollten Namespaces verwendet werden.  
  
 Geschachtelte Typen basieren auf dem Memberzugriff, was von einigen Programmierern nicht verstanden wird.  
  
 Geschützte Typen können in Unterklassen und geschachtelten Typen für die weitere Anpassung verwendet werden.  
  
## Behandeln von Verstößen  
 Wenn Sie nicht beabsichtigen, dass der geschachtelte Typ extern sichtbar sein soll, ändern Sie das Zugriffsverfahren für den Typ.  Andernfalls entfernen Sie den geschachtelten Typ aus seinem übergeordneten Element.  Falls beabsichtigt war, durch die Schachtelung die Kategorisierung des geschachtelten Typs zu bewirken, erstellen Sie die Hierarchie mithilfe eines Namespaces.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]