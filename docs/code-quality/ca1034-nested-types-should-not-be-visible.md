---
title: 'CA1034: Geschachtelte Typen sollten nicht sichtbar sein | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb549e50f33ac172f1eaa0e2a4489cd1900d0542
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Geschachtelte Typen sollten nicht sichtbar sein
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein extern sichtbarer Typ enthält eine extern sichtbarer Typ-Deklaration. Geschachtelte Enumerationen und geschützte Typen sind von dieser Regel ausgenommen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein geschachtelter Typ ist ein Typ, der innerhalb des Bereichs eines anderen Typs deklariert. Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails der enthaltenden Typ haben. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein.  
  
 Verwenden Sie extern sichtbare geschachtelte Typen nicht für logische Gruppierung oder um Namenskonflikte zu vermeiden. Verwenden Sie stattdessen Namespaces.  
  
 Geschachtelte Typen gehören das Konzept von Memberzugriff, die einige Programmierer nicht verstanden werden.  
  
 Geschützte Typen können in Unterklassen und geschachtelte Typen in erweiterte Anpassungsszenarien verwendet werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn Sie nicht, dass den geschachtelten Typ extern sichtbar sein sollen beabsichtigen, ändern Sie den Zugriff des Typs. Entfernen Sie andernfalls den geschachtelten Typ von seinem übergeordneten Element. Ist der Zweck der Schachtelung den geschachtelten Typ kategorisiert, verwenden Sie einen Namespace, um die Hierarchie stattdessen erstellen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]