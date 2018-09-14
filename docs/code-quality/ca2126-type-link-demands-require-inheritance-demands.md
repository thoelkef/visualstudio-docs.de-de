---
title: 'CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82fe9045173e65b24204a3b04e12b6a7f655c651
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548399"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher unversiegelter Typ wird geschützt durch einen Linkaufruf, verfügt über eine überschreibbare Methode, und weder der Typ noch die Methode mit einer vererbungsanforderung geschützt ist.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Linkaufruf auf eine Methode oder der deklarierende Typ ist den direkte Aufrufer der Methode, um die angegebene Berechtigung erforderlich. Eine vererbungsanforderung für eine Methode erfordert eine überschreibende Methode, um die angegebene Berechtigung zu erhalten. Eine vererbungsanforderung für einen Typ ist erforderlich, eine abgeleitete Klasse die angegebene Berechtigung haben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, Sichern Sie den Typ oder die Methode mit einer vererbungsanforderung für die gleichen Berechtigungen wie den Linkaufruf aus.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2108: Deklarative Sicherheit auf Werttypen überprüfen](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)