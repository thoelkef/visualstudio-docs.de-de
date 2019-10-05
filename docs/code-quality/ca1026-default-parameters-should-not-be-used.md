---
title: 'CA1026: Standardparameter sollten nicht verwendet werden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62de7654083f3fd64f95401f95e5ee593effb27d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236130"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Standardparameter sollten nicht verwendet werden.

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein extern sichtbarer Typ enthält eine extern sichtbare Methode, die einen Standardparameter verwendet.

## <a name="rule-description"></a>Regelbeschreibung
Methoden, die Standardparameter verwenden, sind unter dem Common Language Specification (CLS) zulässig. Allerdings können Compiler die Werte, die diesen Parametern zugewiesen sind, durch die CLS ignorieren. Code, der für Compiler geschrieben wird, die Standardparameter Werte ignorieren, muss explizit Argumente für jeden Standardparameter bereitstellen. Um das gewünschte Verhalten für Programmiersprachen beizubehalten, sollten Methoden, die Standardparameter verwenden, durch Methoden Überladungen ersetzt werden, die die Standardparameter bereitstellen.

Der Compiler ignoriert die Werte der Standardparameter für die verwaltete Erweiterung C++ für den Zugriff auf verwalteten Code. Der Visual Basic-Compiler unterstützt Methoden, die über Standardparameter verfügen, die das [optionale](/dotnet/visual-basic/language-reference/modifiers/optional) Schlüsselwort verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die-Methode, die Standardparameter verwendet, mit Methoden Überladungen, die die Standardparameter bereitstellen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Methode, die Standardparameter verwendet, und die überladenen Methoden, die eine äquivalente Funktionalität bereitstellen.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1025: Wiederholende Argumente durch ein Parameter Array ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Siehe auch
[Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)