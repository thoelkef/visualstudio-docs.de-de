---
title: 'CA1019: Accessoren für Attribut Argumente definieren | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534952"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Accessoren für Attributargumente definieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Im Konstruktor definiert ein Attribut Argumente, die keine entsprechenden Eigenschaften haben.

## <a name="rule-description"></a>Beschreibung der Regel
 Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Diese Regel überprüft, ob Sie die entsprechende Eigenschaft für jeden Konstruktorparameter definiert haben.

 Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen.

 Bei obligatorischen und optionalen Argumenten sollten die entsprechenden Eigenschaften und Konstruktorparameter denselben Namen, aber eine unterschiedliche groß-und Kleinschreibung verwenden. Eigenschaften verwenden die Pascal-Schreibweise, und Parameter verwenden Kamel Schreibweise.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine schreibgeschützte Eigenschaft für jeden Konstruktorparameter hinzu, der nicht über einen verfügt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung aus dieser Regel, wenn Sie nicht möchten, dass der Wert des obligatorischen Arguments abgerufen werden kann.

## <a name="custom-attributes-example"></a>Beispiel für benutzerdefinierte Attribute

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt zwei Attribute, die einen obligatorischen (positionellen) Parameter definieren. Die erste Implementierung des-Attributs ist falsch definiert. Die zweite Implementierung ist richtig.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Positions-und benannte Argumente

### <a name="description"></a>BESCHREIBUNG
 Positions-und benannte Argumente machen es für Consumer Ihrer Bibliothek klar, welche Argumente für das Attribut obligatorisch sind und welche Argumente optional sind.

 Das folgende Beispiel zeigt eine Implementierung eines Attributs, das sowohl positionelle als auch benannte Argumente hat.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird gezeigt, wie Sie das benutzerdefinierte Attribut auf zwei Eigenschaften anwenden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1813: Nicht versiegelte Attribute vermeiden.](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Weitere Informationen
 [Attribute](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
