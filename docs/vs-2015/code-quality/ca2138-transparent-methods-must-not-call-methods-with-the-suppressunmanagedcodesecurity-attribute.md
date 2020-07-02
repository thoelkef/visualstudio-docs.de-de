---
title: 'CA2138: transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut abrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546496"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods|
|CheckId|CA2138|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Sicherheits transparente Methode ruft eine Methode auf, die mit dem-Attribut markiert ist <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> .

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel wird für jede transparente Methode ausgelöst, die direkt in systemeigenen Code aufruft, z. b. mithilfe eines über einen P/callaufruf (Platt Form Aufruf). P/Call-und COM-Interop-Methoden, die mit dem-Attribut markiert sind, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> führen dazu, dass LinkDemand für die aufrufende Methode ausgeführt wird. Da der Sicherheits transparente Code linkforderungen nicht erfüllen kann, kann der Code auch keine Methoden aufrufen, die mit dem SuppressUnmanagedCodeSecurity-Attribut gekennzeichnet sind, oder Methoden der Klasse, die mit dem SuppressUnmanagedCodeSecurity-Attribut markiert sind. Die Methode kann nicht ausgeführt werden, oder die Anforderung wird in eine vollständige Anforderung konvertiert.

 Verstöße gegen diese Regel führen zu einem <xref:System.MethodAccessException> im Sicherheits Transparenz Modell der Ebene 2 und einer vollständigen Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenz Modell der Ebene 1.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> -Attribut, und markieren Sie die Methode mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
