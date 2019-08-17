---
title: 'CA1041: ObsoleteAttribute-Meldung bereitstellen.'
ms.date: 03/11/2019
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
ms.openlocfilehash: a0545503b80e2f256593012e06cdf7ccd8b3b5b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547631"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute-Meldung bereitstellen.

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ oder Member wird mit einem <xref:System.ObsoleteAttribute?displayProperty=fullName> -Attribut gekennzeichnet, dessen <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> -Eigenschaft nicht angegeben ist.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen und Member, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.ObsoleteAttribute>wird verwendet, um veraltete Bibliothekstypen und Member zu markieren. Bibliotheks Consumer sollten die Verwendung eines beliebigen Typs oder Members vermeiden, der als veraltet markiert ist. Dies liegt daran, dass Sie möglicherweise nicht unterstützt wird und schließlich aus späteren Versionen der Bibliothek entfernt wird. Wenn ein Typ oder Member, der mit <xref:System.ObsoleteAttribute> markiert ist, kompiliert <xref:System.ObsoleteAttribute.Message%2A> wird, wird die-Eigenschaft des-Attributs angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. Diese Informationen umfassen im Allgemeinen, wie lange der veraltete Typ oder Member von den Bibliotheks-Designern unterstützt wird, und die bevorzugte Ersetzung für die Verwendung von.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen `message` Sie dem <xref:System.ObsoleteAttribute> Konstruktor den Parameter hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung aus dieser Regel, da <xref:System.ObsoleteAttribute.Message%2A> die-Eigenschaft wichtige Informationen über den veralteten Typ oder Member bereitstellt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein veraltetes Element, das über eine <xref:System.ObsoleteAttribute>ordnungsgemäß deklarierte verfügt.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.ObsoleteAttribute?displayProperty=fullName>