---
title: 'CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4e302c9e8cc74d461dc67237bd62b34097c0aceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542182"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine sicherheitstransparente Methode ruft eine Methode, die mit der <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, für jede transparente Methode, die direkt in systemeigenen Code, z. B. mithilfe von P/Invoke zu aufruft (Platform invoke) aufrufen. P/Invoke und COM-Interop-Methoden, die mit markiert sind die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut Ergebnis in einen LinkDemand für die aufrufende Methode ausgeführt wird. Da LinkDemands Sicherheitstransparenter Code nicht erfüllt werden kann, kann nicht der Code auch aufrufen, Methoden, die mit dem SuppressUnmanagedCodeSecurity-Attribut markiert werden oder Methoden der Klasse, die mit dem SuppressUnmanagedCodeSecurity-Attribut markiert ist. Die Methode schlägt fehl, oder die Anforderung wird in einer vollständigen Anforderung konvertiert werden.

 Verstöße gegen diese Regel führen zu einem <xref:System.MethodAccessException> im Transparenzmodell der Ebene 2-Security und einer vollständigen Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenzmodell Ebene 1.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut, und markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]