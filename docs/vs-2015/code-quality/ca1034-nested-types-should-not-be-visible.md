---
title: 'CA1034: die Typen dürfen nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33e7ea6aaefcaf5b6cbf0bf8c52ade0b9e68a549
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661852"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Geschachtelte Typen sollten nicht sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält eine extern sichtbare Typdeklaration. Von dieser Regel ausgenommen sind die von dieser Regel ausgefallenen Enumerationen und geschützten Typen.

## <a name="rule-description"></a>Regelbeschreibung
 Ein geschachtelter Typ ist ein Typ, der innerhalb des Gültigkeits Bereichs eines anderen Typs deklariert wird. Bei der Einkapselung von privaten Implementierungsdetails des enthaltenden Typs sind die Typen von Typen nützlich. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein.

 Verwenden Sie keine extern sichtbaren gruppierten Typen für die logische Gruppierung oder, um Namenskonflikte zu vermeiden. Verwenden Sie stattdessen Namespaces.

 Zu den Typen der Member gehört das Konzept der Member-Barrierefreiheit, die einige Programmierer nicht eindeutig verstehen.

 Geschützte Typen können in vorklassen und in untergeordneten Typen in Szenarios für die vorab Anpassung verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn Sie nicht beabsichtigen, den Typ extern sichtbar zu machen, ändern Sie den Zugriff des Typs. Andernfalls entfernen Sie den vom übergeordneten Typ. Wenn der Zweck der Schachtelung darin besteht, den geschachtelten Typ zu kategorisieren, verwenden Sie stattdessen einen Namespace, um die Hierarchie zu erstellen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
