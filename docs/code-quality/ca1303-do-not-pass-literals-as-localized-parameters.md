---
title: 'CA1303: Literale nicht als lokalisierte Parameter übergeben.'
ms.date: 11/04/2016
ms.topic: reference
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc32db1aea9c5514a7548bc889b65463de3de3d5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714697"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben.

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Methode übergibt ein Zeichenfolgenliteral als Parameter an eine .NET Konstruktor oder eine Methode, und diese Zeichenfolge sollte lokalisierbar sein.

Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert, auf einen Parameter oder eine Eigenschaft übergeben wird und eine oder mehrere der folgenden Fälle zutrifft:

- Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft wird festgelegt auf "true".

- Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Beschriftung".

- Der Name des Parameters, der auf eine Console.Write "oder" Console.WriteLine-Methode übergeben wird, ist "Value" oder "format".

## <a name="rule-description"></a>Regelbeschreibung

Zeichenfolgenliterale, die in Quellcode eingebettet sind, sind schwer zu lokalisieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichenfolge, die durch eine Instanz der abgerufenen der <xref:System.Resources.ResourceManager> Klasse.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Codebibliothek nicht lokalisiert wird oder wenn die Zeichenfolge nicht mit der Endbenutzer oder ein Entwickler, die über die Codebibliothek verbunden ist.

Benutzer können es sich um Rauschen für Methoden entfernt, die nicht lokalisierte Zeichenfolgen übergeben werden sollen, durch das Umbenennen der Parameter oder die Eigenschaft oder markieren diese Elemente als bedingt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eine der zwei Argumente außerhalb des gültigen Bereichs befinden. Für das erste Argument ist wird der Ausnahmekonstruktor eine Literalzeichenfolge, übergeben gegen diese Regel verstößt. Für das zweite Argument, dem Konstruktor wird ordnungsgemäß übergeben eine Zeichenfolge abrufen, der über eine <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Ressourcen in desktop-apps](/dotnet/framework/resources/index)