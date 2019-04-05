---
title: 'CA1303: Literale nicht als lokalisierte Parameter übergeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2ef9eaa8e0921d8ff463478a42eca688d4b952b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959683"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder-Methode in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] -Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein.

 Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert, auf einen Parameter oder eine Eigenschaft übergeben wird und eine oder mehrere der folgenden Fälle zutrifft:

-   Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft wird festgelegt auf "true".

-   Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Beschriftung".

-   Der Name des Parameters, der auf eine Console.Write "oder" Console.WriteLine-Methode übergeben wird, ist "Value" oder "format".

## <a name="rule-description"></a>Regelbeschreibung
 Zeichenfolgenliterale, die in Quellcode eingebettet sind, sind schwer zu lokalisieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichenfolge, die durch eine Instanz der abgerufenen der <xref:System.Resources.ResourceManager> Klasse.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Codebibliothek nicht lokalisiert wird, oder die Zeichenfolge nicht der Endbenutzer oder ein Entwickler, die über die Codebibliothek verfügbar gemacht wird.

 Benutzer können Störungen für Methoden vermeiden, die nicht lokalisierte Zeichenfolgen übergeben werden sollte, Parameters oder der Eigenschaft, die mit dem Namen umbenennen oder markieren diese Elemente als bedingt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eine der zwei Argumente außerhalb des gültigen Bereichs befinden. Für das erste Argument ist wird der Ausnahmekonstruktor eine Literalzeichenfolge, übergeben gegen diese Regel verstößt. Für das zweite Argument, dem Konstruktor wird ordnungsgemäß übergeben eine Zeichenfolge abrufen, der über eine <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Ressourcen in Desktop-Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
