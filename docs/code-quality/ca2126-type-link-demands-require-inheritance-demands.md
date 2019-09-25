---
title: 'CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f01ba5af7640521333093e4bba1f36a95363b60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232469"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen.

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentlicher unversiegelter Typ wird durch einen Link Aufruf geschützt, verfügt über eine über schreibbare Methode, und weder der Typ noch die Methode wird mit einer Vererbungs Anforderung geschützt.

## <a name="rule-description"></a>Regelbeschreibung
Ein Link Aufruf für eine Methode oder Ihren deklarierenden Typ erfordert, dass der unmittelbare Aufrufer der Methode über die angegebene Berechtigung verfügt. Ein Vererbungs Bedarf für eine Methode erfordert, dass eine über schreibende Methode über die angegebene Berechtigung verfügt. Ein Vererbungs Bedarf für einen Typ erfordert, dass eine abgeleitete Klasse über die angegebene Berechtigung verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, sichern Sie den Typ oder die Methode mit einer Vererbungs Anforderung für dieselbe Berechtigung wie der Link Aufruf.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2108: Deklarative Sicherheit für Werttypen überprüfen](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: Methoden mit Link aufrufen nicht indirekt verfügbar machen](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: Überschreibungs Link Aufrufe sollten mit der Basis identisch sein.](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Link Aufrufe](/dotnet/framework/misc/link-demands)