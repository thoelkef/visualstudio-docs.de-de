---
title: 'CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dd12cf43425c863b72c7a77b8ccd8884c0ad7d2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine sicherheitstransparente Methode ruft eine Methode, die mit der <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel wird ausgelöst, für jede transparente Methode, die direkt in systemeigenen Code aufruft, z. B. mit einem über P/Invoke (Platform invoke) aufrufen. P/Invoke und COM-Interop-Methoden, die mit markiert sind die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> -Attribut Ergebnis in einen LinkDemand für die aufrufende Methode ausgeführt wird. Da Sicherheitstransparenter Code LinkDemands erfüllen kann, kann nicht im Code auch aufrufen, mit dem SuppressUnmanagedCodeSecurity-Attribut markierte, Methoden oder Methoden der Klasse, mit dem SuppressUnmanagedCodeSecurity-Attribut markiert ist. Die Methode schlägt fehl, oder die Anforderung wird in einer vollständigen Anforderung konvertiert werden.  
  
 Verstöße gegen diese Regel führen zu einem <xref:System.MethodAccessException> im Transparenzmodell der Ebene-2-Sicherheit zu einer vollständigen Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenzmodell Ebene 1.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut, und markieren Sie die Methode mit der <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]