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
ms.openlocfilehash: a5dc7f7e62526050eeabdb91a557bbdf0fbcf6da
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957951"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Standardparameter sollten nicht verwendet werden.

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält eine extern sichtbare Methode, die einen Standardparameter verwendet werden.

## <a name="rule-description"></a>Regelbeschreibung
 Methoden, die Standardparameter verwenden, sind unter der Common Language Specification (CLS) zulässig. die CLS lässt jedoch Compiler, um die Werte zu ignorieren, die diese Parameter zugewiesen werden. Code, der für Compiler geschrieben wird, die ignoriert werden Standardparameterwerte muss die Argumente für jeden Standardparameter explizit bereitgestellt werden. Um das Verhalten zu gewährleisten, das verschiedenen Programmiersprachen werden sollen, sollte Methoden, die Standardparameter verwenden durch methodenüberladungen ersetzt werden, die die Standardparameter bereitgestellt.

 Der Compiler ignoriert die Werte der Standardparameter für Managed Extensions für C++, beim Zugriff auf verwaltetem Code. Visual Basic-Compiler unterstützt Methoden, die standardmäßigen Parameter verfügen, verwenden die [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) Schlüsselwort.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ersetzen Sie die Methode, die Standardparameter durch überladene Methoden verwendet werden, die die Standardparameter angeben, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die Standardparameter verwendet und die überladene Methoden, die eine entsprechende Funktionalität bereitzustellen.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Siehe auch
 [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)