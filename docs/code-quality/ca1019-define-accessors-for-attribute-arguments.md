---
title: 'CA1019: Accessoren für Attributargumente definieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e9491a608087565e84274d47c601b0629737d2f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942478"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Accessoren für Attributargumente definieren.

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 In seinem Konstruktor definiert ein Attribut Argumente, die nicht über die entsprechende Eigenschaften verfügen.

## <a name="rule-description"></a>Regelbeschreibung
 Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Diese Regel überprüft, dass für jeden Konstruktorparameter, Sie die entsprechende Eigenschaft definiert haben.

 Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen.

 Der gleiche name jedoch unterschiedlichen Groß-/Kleinschreibung, für obligatorischen und optionalen Argumenten, die entsprechenden Eigenschaften und Konstruktorparameter verwendet werden soll. Verwenden der Pascal-Schreibweise Eigenschaften Groß-/Kleinschreibung und Parameter Kamel-Schreibweise verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine nur-Lese Eigenschaft für jeden Konstruktorparameter, die nicht vorhanden ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass der Wert, der das erforderliche Argument abgerufen werden möchten.

## <a name="custom-attributes-example"></a>Beispiel für benutzerdefinierte Attribute

Das folgende Beispiel zeigt zwei Attribute, die einen obligatorischen Parameter für die (mit Feldern fester Breite) zu definieren. Die erste Implementierung des Attributs ist nicht ordnungsgemäß definiert. Die zweite Implementierung ist richtig.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Positionelle und benannte Argumente

Positionelle und benannte Argumente machen es klar, auf Consumer Ihrer Bibliothek, die die Argumente für das Attribut erforderlich sind und welche Argumente sind optional.

Das folgende Beispiel zeigt eine Implementierung der ein Attribut mit benannten und Positionsargumenten:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

Das folgende Beispiel zeigt, wie Sie das benutzerdefinierte Attribut auf zwei Eigenschaften anwenden:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Siehe auch
 [Attribute](/dotnet/standard/design-guidelines/attributes)