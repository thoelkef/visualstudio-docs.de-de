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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661449"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Literale nicht als lokalisierte Parameter übergeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode übergibt ein Zeichenfolgenliteralzeichen als Parameter an einen Konstruktor oder eine Methode in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek, und diese Zeichenfolge muss lokalisiert werden können.

 Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert an einen Parameter oder eine Eigenschaft übergeben wird und mindestens einer der folgenden Fälle zutrifft:

- Das <xref:System.ComponentModel.LocalizableAttribute>-Attribut des-Parameters oder der-Eigenschaft ist auf true festgelegt.

- Der Parameter-oder Eigenschaftsname enthält "Text", "Message" oder "Caption".

- Der Name des Zeichen folgen Parameters, der an eine Console. Write-oder Console. Write teline-Methode übergeben wird, ist entweder "Value" oder "Format".

## <a name="rule-description"></a>Regelbeschreibung
 Zeichen folgen Literale, die in Quellcode eingebettet sind, sind schwer zu lokalisieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichenfolge, die durch eine Instanz der <xref:System.Resources.ResourceManager>-Klasse abgerufen wurde

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Code Bibliothek nicht lokalisiert wird, oder wenn die Zeichenfolge für den Endbenutzer oder einen Entwickler, der die Code Bibliothek verwendet, nicht verfügbar gemacht wird.

 Benutzer können das Rauschen gegen Methoden vermeiden, die lokalisierte Zeichen folgen nicht übergeben werden sollen, indem Sie entweder den Parameter oder die Eigenschaft mit dem Namen umbenennen oder diese Elemente als bedingt markieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eines der beiden Argumente außerhalb des gültigen Bereichs liegt. Für das erste Argument wird dem Ausnahmekonstruktor eine Literalzeichenfolge übergeben, die gegen diese Regel verstößt. Für das zweite Argument wird dem Konstruktor ordnungsgemäß eine Zeichenfolge übergeben, die durch eine <xref:System.Resources.ResourceManager> abgerufen wurde.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Ressourcen in Desktop-Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
