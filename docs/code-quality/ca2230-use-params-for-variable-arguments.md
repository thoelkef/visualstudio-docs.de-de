---
title: "CA2230: Params für Variablenargumente verwenden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d578a68cfa5ff6b29d3e625dfd00b76e9994240a
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: params für Variablenargumente verwenden
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, verwendet die `VarArgs` Aufrufkonvention.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die `VarArgs` -Aufrufkonvention mit bestimmten Methodendefinitionen, die eine Variable von Parametern Anzahl verwendet wird. Eine Methode mit dem `VarArgs` Aufrufkonvention Common Language Specification (CLS) kompatibel ist und möglicherweise nicht in verschiedenen Programmiersprachen zugegriffen werden.  
  
 In c# ist die `VarArgs` -Aufrufkonvention wird verwendet, wenn die Parameterliste einer Methode mit endet die `__arglist` Schlüsselwort. Visual Basic unterstützt nicht die `VarArgs` Aufrufkonvention und Visual C++ können Sie dessen Verwendung nur in nicht verwaltetem Code, das die Ellipse verwendet `...` Notation.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel in c# zu beheben, verwenden Sie die [Params](/dotnet/csharp/language-reference/keywords/params) -Schlüsselwort anstelle von `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Methoden, die die Regel verletzt und eine, die die Regel erfüllt.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)