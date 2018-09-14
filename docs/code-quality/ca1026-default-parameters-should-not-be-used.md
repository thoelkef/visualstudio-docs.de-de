---
title: 'CA1026: Standardparameter sollten nicht verwendet werden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faced51a807a69ecc2e11a04e9ed5e292f4d3a19
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547606"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Standardparameter sollten nicht verwendet werden
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