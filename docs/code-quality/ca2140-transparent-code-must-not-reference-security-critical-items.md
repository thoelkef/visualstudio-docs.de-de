---
title: 'CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232146"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.

|||
|-|-|
|TypeName|Transparentmethodsmustnotreferencecriticalcode|
|CheckId|CA2140|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine transparente Methode:

- behandelt einen sicherheitskritischen Sicherheits Ausnahmetyp.

- verfügt über einen Parameter, der als sicherheitskritischer Typ markiert ist.

- verfügt über einen generischen Parameter mit sicherheitskritischen Einschränkungen

- verfügt über eine lokale Variable mit einem sicherheitskritischen Typ.

- verweist auf einen Typ, der als sicherheitskritisch markiert ist.

- Ruft eine Methode auf, die als sicherheitskritisch markiert ist.

- verweist auf ein Feld, das als sicherheitskritisch markiert ist.

- Gibt einen Typ zurück, der als sicherheitskritisch markiert ist.

## <a name="rule-description"></a>Regelbeschreibung

Ein Code Element, das mit dem <xref:System.Security.SecurityCriticalAttribute> -Attribut markiert ist, ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden <xref:System.TypeAccessException>, <xref:System.MethodAccessException> wird eine <xref:System.FieldAccessException> , oder ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Führen Sie einen der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

- Markieren Sie das Code Element, das den sicherheitskritischen Code verwendet <xref:System.Security.SecurityCriticalAttribute> , mit dem-Attribut.

     \- oder –

- Entfernen Sie <xref:System.Security.SecurityCriticalAttribute> das Attribut aus den Code Elementen, die als sicherheitskritisch gekennzeichnet sind, und markieren Sie <xref:System.Security.SecuritySafeCriticalAttribute> Sie <xref:System.Security.SecurityTransparentAttribute> stattdessen mit dem-Attribut oder dem-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

In den folgenden Beispielen versucht eine transparente Methode, auf eine sicherheitskritische generische Auflistung, ein Sicherheitskritisches Feld und eine sicherheitskritische Methode zu verweisen.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>