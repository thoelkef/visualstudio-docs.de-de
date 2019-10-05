---
title: 'CA2111: Zeiger sollten nicht sichtbar sein.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a93f776ac6e133b0ebf79d1dfa56f802ff66e5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232770"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Zeiger sollten nicht sichtbar sein.

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentliches oder geschütztes <xref:System.IntPtr?displayProperty=fullName> Feld <xref:System.UIntPtr?displayProperty=fullName> oder ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.IntPtr>und <xref:System.UIntPtr> sind Zeiger Typen, die für den Zugriff auf nicht verwalteten Speicher verwendet werden. Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann bösartiger Code den Wert des Zeigers ändern und möglicherweise den Zugriff auf beliebige Speicherorte im Arbeitsspeicher erlauben oder Anwendungs-oder Systemfehler verursachen.

Wenn Sie den Zugriff auf den Typ, der das Zeiger Feld enthält, sichern möchten [, finden Sie weitere Informationen unter CA2112: Gesicherte Typen sollten keine Felder](../code-quality/ca2112-secured-types-should-not-expose-fields.md)verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Sichern Sie den Zeiger, indem Sie ihn als schreibgeschützt, intern oder privat festlegen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrückt eine Warnung aus dieser Regel, wenn Sie sich nicht auf den Wert des Zeigers verlassen.

## <a name="example"></a>Beispiel
Der folgende Code zeigt Zeiger, die die Regel verletzen und erfüllen. Beachten Sie, dass die nicht privaten Zeiger auch gegen die [Regel CA1051 verstoßen: Deklarieren Sie keine sichtbaren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)Instanzfelder.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>