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
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235113"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben.

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode übergibt ein Zeichenfolgenliteralzeichen als Parameter an einen .net-Konstruktor oder eine Methode, und diese Zeichenfolge muss lokalisierbar sein.

Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert an einen Parameter oder eine Eigenschaft übergeben wird und mindestens einer der folgenden Fälle zutrifft:

- Das <xref:System.ComponentModel.LocalizableAttribute> -Attribut des-Parameters oder der-Eigenschaft ist auf true festgelegt.

- Der Parameter-oder Eigenschaftsname enthält "Text", "Message" oder "Caption".

- Der Name des Zeichen folgen Parameters, der an eine Console. Write-oder Console. Write teline-Methode übergeben wird, ist entweder "Value" oder "Format".

## <a name="rule-description"></a>Regelbeschreibung

Zeichen folgen Literale, die in Quellcode eingebettet sind, sind schwer zu lokalisieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichen <xref:System.Resources.ResourceManager> Folge, die durch eine Instanz der-Klasse abgerufen wurde

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Code Bibliothek nicht lokalisiert wird, oder wenn die Zeichenfolge für den Endbenutzer oder einen Entwickler, der die Code Bibliothek verwendet, nicht verfügbar gemacht wird.

Benutzer können das Rauschen gegen Methoden eliminieren, denen keine lokalisierten Zeichen folgen übergeben werden sollen, indem Sie entweder den Parameter oder die Eigenschaft umbenennen oder diese Elemente als bedingt markieren.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eines der beiden Argumente außerhalb des gültigen Bereichs liegt. Für das erste Argument wird dem Ausnahmekonstruktor eine Literalzeichenfolge übergeben, die gegen diese Regel verstößt. Für das zweite Argument wird dem Konstruktor ordnungsgemäß eine Zeichenfolge übergeben, die <xref:System.Resources.ResourceManager>über eine abgerufen wurde.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)