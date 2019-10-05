---
title: 'CA1018: Attribute mit AttributeUsageAttribute markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a1ed8610ce84279f5fde3b802d976a3e766d99
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236241"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Attribute mit AttributeUsageAttribute markieren.

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Das <xref:System.AttributeUsageAttribute?displayProperty=fullName> -Attribut ist für das benutzerdefinierte Attribut nicht vorhanden.

## <a name="rule-description"></a>Regelbeschreibung
Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie <xref:System.AttributeUsageAttribute> es mithilfe von, um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. Beispielsweise können Sie ein Attribut definieren, mit dem die Person identifiziert wird, die für die Verwaltung und Erweiterung der einzelnen Typen in einer Bibliothek zuständig ist, und dass die Verantwortlichkeit immer auf der Typebene zugewiesen wird. In diesem Fall sollten Compiler das-Attribut für Klassen, Enumerationen und Schnittstellen aktivieren, diese aber nicht für Methoden, Ereignisse oder Eigenschaften aktivieren. Organisations Richtlinien und-Prozeduren würden vorschreiben, ob das Attribut für Assemblys aktiviert werden soll.

Die <xref:System.AttributeTargets?displayProperty=fullName> -Enumeration definiert die Ziele, die Sie für ein benutzerdefiniertes Attribut angeben können. Wenn Sie weglassen <xref:System.AttributeUsageAttribute>, ist das benutzerdefinierte Attribut für alle Ziele gültig, wie durch den `All` Wert der <xref:System.AttributeTargets> -Enumeration definiert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, geben Sie Ziele für das- <xref:System.AttributeUsageAttribute>Attribut an, indem Sie verwenden. Weitere Informationen finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Sie sollten einen Verstoß gegen diese Regel beheben, anstatt die Meldung auszuschließen. Auch wenn das Attribut erbt <xref:System.AttributeUsageAttribute>, sollte das-Attribut vorhanden sein, um die Code Verwaltung zu vereinfachen.

## <a name="example"></a>Beispiel
Im folgenden Beispiel werden zwei Attribute definiert. `BadCodeMaintainerAttribute`lässt die <xref:System.AttributeUsageAttribute> Anweisung falsch aus und implementiert `GoodCodeMaintainerAttribute` das-Attribut, das weiter oben in diesem Abschnitt beschrieben wird. Beachten Sie, dass `DeveloperName` die-Eigenschaft für die Entwurfs [Regel CA1019 erforderlich ist: Definieren Sie Accessoren für Attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) Argumente und ist aus Gründen der Vollständigkeit enthalten.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1019: Accessoren für Attribut Argumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Siehe auch

- [Attribute](/dotnet/standard/design-guidelines/attributes)