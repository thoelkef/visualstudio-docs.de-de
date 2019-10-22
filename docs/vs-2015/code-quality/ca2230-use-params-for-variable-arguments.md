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
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662829"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: params für Variablenargumente verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die die `VarArgs`-Aufruf Konvention verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 Die `VarArgs`-Aufruf Konvention wird mit bestimmten Methoden Definitionen verwendet, die eine Variable Anzahl von Parametern akzeptieren. Eine Methode, die die `VarArgs`-Aufruf Konvention verwendet, ist nicht Common Language Specification (CLS) kompatibel und ist möglicherweise nicht über Programmiersprachen zugänglich.

 In C#wird die `VarArgs`-Aufruf Konvention verwendet, wenn die Parameterliste einer Methode mit dem Schlüsselwort `__arglist` endet. Visual Basic unterstützt die `VarArgs`-Aufruf Konvention nicht, und C++ Visual ermöglicht die Verwendung nur in nicht verwaltetem Code, der die Ellipse `...`-Notation verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel in C#zu beheben, verwenden Sie das Schlüsselwort " [para](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) " anstelle von "`__arglist`".

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, eine, die gegen die Regel verstößt, und eine, die die Regel erfüllt.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Sprachen Unabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
