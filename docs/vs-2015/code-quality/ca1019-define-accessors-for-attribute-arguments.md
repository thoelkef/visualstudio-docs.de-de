---
title: 'CA1019: Accessors für Attributargumente definieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4c21a3e4daeea64dd36c42bd986fcda75ad0bcaa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960574"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Accessoren für Attributargumente definieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass der Wert, der das erforderliche Argument abgerufen werden möchten.

## <a name="custom-attributes-example"></a>Beispiel für benutzerdefinierte Attribute

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt zwei Attribute, die einen obligatorischen Parameter für die (mit Feldern fester Breite) zu definieren. Die erste Implementierung des Attributs ist nicht ordnungsgemäß definiert. Die zweite Implementierung ist richtig.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Positionelle und benannte Argumente

### <a name="description"></a>Beschreibung
 Positionelle und benannte Argumente stellen für Consumer Ihrer Bibliothek gelöscht wird, welche Argumente sind für das Attribut obligatorisch und welche Argumente sind optional.

 Das folgende Beispiel zeigt eine Implementierung der ein Attribut mit benannten und Positionsargumenten.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Kommentare
 Das folgende Beispiel zeigt, wie Sie das benutzerdefinierte Attribut auf zwei Eigenschaften anwenden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Siehe auch
 [Attribute](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
