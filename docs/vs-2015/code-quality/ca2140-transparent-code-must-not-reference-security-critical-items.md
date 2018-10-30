---
title: 'CA2140: Transparenter Code darf nicht sicherheitskritische Elemente verweisen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb6c01fc281384aec28ae46dbb1466686626df8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892115"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode:

-   verarbeitet einen Sicherheit sicherheitsrelevanten Ausnahmetyp

-   verfügt über einen Parameter, der als einen sicherheitskritischen Typ gekennzeichnet ist.

-   verfügt über einen generischen Parameter mit einem kritischen sicherheitseinschränkungen

-   verfügt über eine lokale Variable, der einen sicherheitskritischen Typ

-   verweist auf einen Typ, der als sicherheitskritisch markiert ist

-   Ruft eine Methode, die als sicherheitskritisch markiert ist

-   verweist auf ein Feld, die als sicherheitskritisch markiert ist

-   Gibt einen Typ, der als sicherheitskritisch markiert ist

## <a name="rule-description"></a>Regelbeschreibung
 Ein Codeelement an, die mit der <xref:System.Security.SecurityCriticalAttribute> -Attribut ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden eine <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , oder <xref:System.FieldAccessException> ausgelöst wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Führen Sie eine der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

-   Markieren Sie das Codeelement, das die sicherheitskritischem Code mit verwendet die <xref:System.Security.SecurityCriticalAttribute> Attribut

     \- oder –

-   Entfernen Sie die <xref:System.Security.SecurityCriticalAttribute> Attribut aus den Codeelementen, die als sicherheitskritisch markiert sind, und markieren Sie sie mit stattdessen die <xref:System.Security.SecuritySafeCriticalAttribute> oder <xref:System.Security.SecurityTransparentAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Eine transparente Methode versucht, in den folgenden Beispielen wird eine generische Auflistung mit Sicherheit wichtig, ein sicherheitskritisches Feld und eine wichtige Methode verweisen.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>



