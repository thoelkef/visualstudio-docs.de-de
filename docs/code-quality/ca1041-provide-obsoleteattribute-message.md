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
ms.openlocfilehash: ad693014a7f6c16484f03c2d2f746c8159cf160e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873080"
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

Diese Regel nur sucht standardmäßig an extern sichtbare Typen und Member, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.ObsoleteAttribute> Dient zum Kennzeichnen als veraltet markierte von Bibliothekstypen und Member. Consumer sollten die Verwendung von einem beliebigen Typ oder Member, der als veraltet markiert ist. Dies ist, da er möglicherweise nicht unterstützt und in späteren Versionen der Bibliothek entfernt werden. Wenn ein Typ oder Member mit markiert <xref:System.ObsoleteAttribute> kompiliert wurde, die <xref:System.ObsoleteAttribute.Message%2A> -Eigenschaft des Attributs wird angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. Diese Informationen umfassen im Allgemeinen, wie langen den veralteten Typ oder Member wird von der Bibliotheks-Designer und die bevorzugte Ersetzung verwenden unterstützt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen die `message` Parameter, um die <xref:System.ObsoleteAttribute> Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel nicht, da die <xref:System.ObsoleteAttribute.Message%2A> Eigenschaft enthält wichtige Informationen zu den veralteten Typ oder Member.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1041.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen veralteten Member, die einer ordnungsgemäß deklarierten <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.ObsoleteAttribute?displayProperty=fullName>