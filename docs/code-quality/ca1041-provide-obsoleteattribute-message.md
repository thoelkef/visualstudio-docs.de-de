---
title: 'CA1041: ObsoleteAttribute-Meldung bereitstellen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bb8281cb299b9b6ada7470deca82b9158fb323d1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953099"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute-Meldung bereitstellen.

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Einen Typ oder Member ist markiert, indem eine <xref:System.ObsoleteAttribute?displayProperty=fullName> -Attribut, das nicht der <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> angegebene Eigenschaft.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.ObsoleteAttribute> Dient zum Kennzeichnen als veraltet markierte von Bibliothekstypen und Member. Consumer sollten die Verwendung von einem beliebigen Typ oder Member, der als veraltet markiert ist. Dies ist, da er möglicherweise nicht unterstützt und in späteren Versionen der Bibliothek entfernt werden. Wenn ein Typ oder Member mit markiert <xref:System.ObsoleteAttribute> kompiliert wurde, die <xref:System.ObsoleteAttribute.Message%2A> -Eigenschaft des Attributs wird angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. Diese Informationen umfassen im Allgemeinen, wie langen den veralteten Typ oder Member wird von der Bibliotheks-Designer und die bevorzugte Ersetzung verwenden unterstützt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen die `message` Parameter, um die <xref:System.ObsoleteAttribute> Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nicht, da die <xref:System.ObsoleteAttribute.Message%2A> Eigenschaft enthält wichtige Informationen zu den veralteten Typ oder Member.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen veralteten Member, die einer ordnungsgemäß deklarierten <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Siehe auch
 <xref:System.ObsoleteAttribute?displayProperty=fullName>