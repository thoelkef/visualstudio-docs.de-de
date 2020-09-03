---
title: 'CA2230: params für Variablen Argumente verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540360"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: params für Variablenargumente verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die die `VarArgs` Aufruf Konvention verwendet.

## <a name="rule-description"></a>Beschreibung der Regel
 Die `VarArgs` Aufruf Konvention wird mit bestimmten Methoden Definitionen verwendet, die eine Variable Anzahl von Parametern akzeptieren. Eine Methode, die die `VarArgs` Aufruf Konvention verwendet, ist nicht Common Language Specification (CLS) kompatibel und ist möglicherweise nicht über Programmiersprachen zugänglich.

 In c# wird die `VarArgs` -Aufruf Konvention verwendet, wenn die Parameterliste einer Methode mit dem- `__arglist` Schlüsselwort endet. Visual Basic unterstützt die `VarArgs` Aufruf Konvention nicht, und Visual C++ ermöglicht die Verwendung nur in nicht verwaltetem Code, der die Ellipse- `...` Notation verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel in c# zu beheben, verwenden Sie das Schlüsselwort " [para](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) " anstelle von `__arglist` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, eine, die gegen die Regel verstößt, und eine, die die Regel erfüllt.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Sprachunabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
