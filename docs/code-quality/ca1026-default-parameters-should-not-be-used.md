---
title: 'CA1026: Standardparameter sollten nicht verwendet werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d7a850c959787282cdf6f9d24b392ef4684b7dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Standardparameter sollten nicht verwendet werden
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein extern sichtbarer Typ enthält eine extern sichtbare Methode, die einen Standardparameter verwendet.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Methoden, die Standardparameter verwenden unter der Common Language Specification (CLS) zulässig. die CLS lässt jedoch Compiler, um die Werte zu ignorieren, die diesen Parametern zugewiesen sind. Code, der für Compiler geschrieben wird, die Standardparameterwerte ignorieren muss die Argumente für jeden Standardparameter explizit angeben. Um das Verhalten zu verwalten, das gewünschten verschiedenen Programmiersprachen, sollte der Methoden, die Standardparameter verwenden durch methodenüberladungen ersetzt werden, die die Standardparameter bereitgestellt.  
  
 Der Compiler ignoriert die Werte der Standardparameter für Managed Extensions für C++, wenn sie verwalteten Code zugreift. Visual Basic-Compiler unterstützt Methoden, die Standardparameter vorhanden sind, verwenden die [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) Schlüsselwort.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die Methode, die Standardparameter mit Überladungen der Methode verwendet, die die Standardparameter angeben.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die Standardparameter verwendet, und die überladene Methoden, die eine entsprechende Funktionalität bereitzustellen.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Sprachunabhängigkeit und sprachunabhängige Komponenten](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)