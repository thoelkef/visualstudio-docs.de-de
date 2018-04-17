---
title: 'CA1303: Literale nicht übergeben als lokalisierte Parameter | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1af1edcd86d73687e24619d7e998fe304f9b5787
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder eine Methode in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] -Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein.  
  
 Diese Warnung wird ausgelöst, wenn eine literale Zeichenfolge als Wert, um einen Parameter oder die Eigenschaft übergeben wird und eine oder mehrere der folgenden Fälle zutrifft:  
  
-   Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft ist festgelegt auf "true".  
  
-   Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Caption".  
  
-   Der Name des Parameters, der an eine Console.Write oder Console.WriteLine-Methode übergeben wird, ist "Value" oder "format".  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Zeichenfolgenliterale, die im Quellcode eingebettet sind, sind schwer zu lokalisieren.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral mit einer Zeichenfolge abgerufen, die über eine Instanz der <xref:System.Resources.ResourceManager> Klasse.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die Codebibliothek nicht lokalisiert wird, oder wenn die Zeichenfolge für den Endbenutzer oder ein Entwickler, die über die Codebibliothek nicht bereitgestellt wird.  
  
 Benutzer können Rauschen für Methoden vermeiden, die nicht lokalisierte Zeichenfolgen durch das Umbenennen der Parameter oder eine Eigenschaft mit dem Namen, oder markieren diese Elemente als bedingte übergeben werden soll.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eine der zwei Argumente außerhalb des gültigen Bereichs ist. Als erstes Argument wird die Ausnahmekonstruktor eine literale Zeichenfolge übergeben, die gegen diese Regel verstößt. Für das zweite Argument ist der Konstruktor eine Zeichenfolge, die über abgerufen ordnungsgemäß übergeben einer <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)