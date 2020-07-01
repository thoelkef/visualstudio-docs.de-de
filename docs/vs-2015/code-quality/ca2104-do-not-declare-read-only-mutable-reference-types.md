---
title: 'CA2104: schreibgeschützte änderbare Referenztypen nicht deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521042"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die- <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Sie enthält Member, die den Wert einer Instanz der-Klasse ändern können. Ein Beispiel für einen unveränderlichen Verweistyp ist die- <xref:System.String?displayProperty=fullName> Klasse. Nachdem Sie instanziiert wurde, kann sich der Wert nie ändern.

 Der schreibgeschützte Modifizierer ([Schreib](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) [geschützt in c#, Schreib](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) geschützt in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] und [Konstanten](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) in C++) in einem Verweistyp Feld (Zeiger in C++) verhindert, dass das Feld durch eine andere Instanz des Verweis Typs ersetzt wird. Der-Modifizierer verhindert jedoch nicht, dass die Instanzdaten des Felds durch den Verweistyp geändert werden.

 Felder mit Schreib geschütztem Array sind von dieser Regel ausgenommen, führen jedoch zu einem Verstoß gegen [CA2105: Array Felder dürfen nicht](../code-quality/ca2105-array-fields-should-not-be-read-only.md) schreibgeschützt sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer, oder ersetzen Sie das Feld durch einen unveränderlichen Typ, wenn ein Breaking Change akzeptabel ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Feldtyp unveränderlich ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Feld Deklaration, die einen Verstoß gegen diese Regel verursacht.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
