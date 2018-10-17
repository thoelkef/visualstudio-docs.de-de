---
title: 'CA1303: Literale nicht als lokalisierte Parameter übergeben'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8716a16ea3b141e7c5053e526d92531d0a77bc1e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859405"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder-Methode in der .NET Framework-Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein.

 Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert, auf einen Parameter oder eine Eigenschaft übergeben wird und eine oder mehrere der folgenden Fälle zutrifft:

- Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft wird festgelegt auf "true".

- Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Beschriftung".

- Der Name des Parameters, der auf eine Console.Write "oder" Console.WriteLine-Methode übergeben wird, ist "Value" oder "format".

## <a name="rule-description"></a>Regelbeschreibung
 Zeichenfolgenliterale, die in Quellcode eingebettet sind, sind schwer zu lokalisieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichenfolge, die durch eine Instanz der abgerufenen der <xref:System.Resources.ResourceManager> Klasse.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Codebibliothek nicht lokalisiert wird, oder die Zeichenfolge nicht der Endbenutzer oder ein Entwickler, die über die Codebibliothek verfügbar gemacht wird.

 Benutzer können es sich um Rauschen für Methoden entfernt, die nicht lokalisierte Zeichenfolgen übergeben werden sollen, Parameters oder der Eigenschaft, die mit dem Namen umbenennen oder markieren diese Elemente als bedingt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eine der zwei Argumente außerhalb des gültigen Bereichs befinden. Für das erste Argument ist wird der Ausnahmekonstruktor eine Literalzeichenfolge, übergeben gegen diese Regel verstößt. Für das zweite Argument, dem Konstruktor wird ordnungsgemäß übergeben eine Zeichenfolge abrufen, der über eine <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)