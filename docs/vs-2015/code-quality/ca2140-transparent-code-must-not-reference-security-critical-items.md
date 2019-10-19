---
title: 'CA2140: transparenter Code darf nicht auf sicherheitskritische Elemente verweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602869"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Ein Code Element, das mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut markiert ist, ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden, wird eine <xref:System.TypeAccessException>, <xref:System.MethodAccessException> oder <xref:System.FieldAccessException> ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Führen Sie einen der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

- Markieren Sie das Code Element, das den sicherheitskritischen Code verwendet, mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut.

     \- oder -

- Entfernen Sie das <xref:System.Security.SecurityCriticalAttribute>-Attribut aus den Code Elementen, die als sicherheitskritisch gekennzeichnet sind, und markieren Sie Sie stattdessen mit dem <xref:System.Security.SecuritySafeCriticalAttribute>-oder <xref:System.Security.SecurityTransparentAttribute>-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen versucht eine transparente Methode, auf eine sicherheitskritische generische Auflistung, ein Sicherheitskritisches Feld und eine sicherheitskritische Methode zu verweisen.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
