---
title: "CA1501: &#220;berm&#228;&#223;ige Vererbung vermeiden | Microsoft Docs"
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
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1501: &#220;berm&#228;&#223;ige Vererbung vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief.  
  
## Regelbeschreibung  
 Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein.  Diese Regel schränkt die Analyse auf Hierarchien im selben Modul ein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem Basistyp ab, der sich weniger tief in der Vererbungshierarchie befindet, oder entfernen Sie einige der mittleren Basistypen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  Der Code könnte jedoch schwieriger beizubehalten sein.  Je nach Sichtbarkeit der Typen können durch das Beheben von Verstößen gegen diese Regel unterbrechende Änderungen verursacht werden.  So ist beispielsweise das Entfernen öffentlicher Basistypen eine unterbrechende Änderung.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]