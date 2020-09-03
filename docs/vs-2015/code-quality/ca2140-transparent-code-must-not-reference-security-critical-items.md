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
ms.openlocfilehash: 6f11125f43fd06b0442d1c40cbd4da41e346fd1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546457"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Transparentmethodsmustnotreferencecriticalcode|
|CheckId|CA2140|
|Category|Microsoft.Security|
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

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Code Element, das mit dem-Attribut markiert ist, <xref:System.Security.SecurityCriticalAttribute> ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden <xref:System.TypeAccessException> , <xref:System.MethodAccessException> wird eine, oder <xref:System.FieldAccessException> ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Führen Sie einen der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

- Markieren Sie das Code Element, das den sicherheitskritischen Code verwendet, mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut.

     \- oder -

- Entfernen <xref:System.Security.SecurityCriticalAttribute> Sie das Attribut aus den Code Elementen, die als sicherheitskritisch gekennzeichnet sind, und markieren Sie Sie stattdessen mit dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut oder dem- <xref:System.Security.SecurityTransparentAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen versucht eine transparente Methode, auf eine sicherheitskritische generische Auflistung, ein Sicherheitskritisches Feld und eine sicherheitskritische Methode zu verweisen.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
