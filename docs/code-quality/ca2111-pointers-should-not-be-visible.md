---
title: 'CA2111: Zeiger sollten nicht sichtbar sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a08d15ec491bb78c2d9398c8e689015c9523a3c1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546823"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Zeiger sollten nicht sichtbar sein.

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.IntPtr> und <xref:System.UIntPtr> sind Zeigertypen, die für den Zugriff auf nicht verwalteten Speicher. Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann bösartiger Code den Wert des Zeigers, potenziell den Zugriff auf beliebige Speicherbereiche ermöglichen oder Anwendungs-bzw. Systemfehler verursachen ändern.

 Wenn Sie zum Absichern des Zugriffs auf den Typ, die das Mauszeiger-Feld enthält beabsichtigen, finden Sie unter [CA2112: gesicherte Typen sollten keine Felder verfügbar](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sichern Sie den Zeiger, durch die somit schreibgeschützt, intern oder privat.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht auf den Wert des Zeigers angewiesen sind.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt, Zeiger, die gegen die Regel eingehalten wird. Beachten Sie, dass die nicht privater Zeiger auch die Regel verletzen [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>