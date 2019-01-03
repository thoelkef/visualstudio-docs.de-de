---
title: 'CA1034: Geschachtelte Typen sollten nicht sichtbar sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cce4f148311c301607c57a77aac46787e0578391
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890942"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Geschachtelte Typen sollten nicht sichtbar sein.

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein extern sichtbarer Typ enthält eine extern sichtbarer Typ-Deklaration. Geschachtelte Enumerationen und geschützte Typen sind von dieser Regel ausgenommen.

## <a name="rule-description"></a>Regelbeschreibung
 Ein geschachtelter Typ ist ein Typ, der innerhalb des Bereichs eines anderen Typs deklariert. Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails des enthaltenden Typs. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein.

 Verwenden Sie keine extern sichtbare geschachtelte Typen, für die logische Gruppierung oder so Namenskonflikte zu vermeiden. Verwenden Sie stattdessen Namespaces.

 Geschachtelte Typen enthalten, das Konzept der Member der Barrierefreiheit, die einige Programmierer nicht verstanden werden.

 Geschützte Typen können in Unterklassen und geschachtelte Typen in erweiterte Anpassungsszenarien verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn Sie nicht beabsichtigen, den geschachtelten Typ extern sichtbar sein wird, ändern Sie den Zugriff des Typs. Andernfalls entfernen Sie den geschachtelten Typ von seinem übergeordneten Element. Ist der Zweck der Schachtelung den geschachtelten Typ kategorisiert, verwenden Sie einen Namespace, um die Hierarchie stattdessen zu erstellen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]