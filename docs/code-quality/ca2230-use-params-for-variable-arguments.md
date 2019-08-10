---
title: 'CA2230: params für Variablenargumente verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 505aa8cdc1371a3bc288772d77b49eb7a50e9830
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920147"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: params für Variablenargumente verwenden.

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die die `VarArgs` Aufruf Konvention verwendet.

## <a name="rule-description"></a>Regelbeschreibung
Die `VarArgs` Aufruf Konvention wird mit bestimmten Methoden Definitionen verwendet, die eine Variable Anzahl von Parametern akzeptieren. Eine Methode, die `VarArgs` die Aufruf Konvention verwendet, ist nicht Common Language Specification (CLS) kompatibel und ist möglicherweise nicht über Programmiersprachen zugänglich.

In C#wird die `VarArgs` -Aufruf Konvention verwendet, wenn die Parameterliste einer Methode mit dem `__arglist` -Schlüsselwort endet. Visual Basic unterstützt die `VarArgs` Aufruf Konvention nicht, und Visual C++ ermöglicht die Verwendung nur in nicht verwaltetem Code, der die Ellipse `...` -Notation verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel in C#zu beheben, verwenden Sie das Schlüsselwort " `__arglist` [para](/dotnet/csharp/language-reference/keywords/params) " anstelle von.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt zwei Methoden, eine, die gegen die Regel verstößt, und eine, die die Regel erfüllt.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)