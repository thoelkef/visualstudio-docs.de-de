---
title: "CA1411: COM-Registrierungsmethoden dürfen nicht sein sichtbar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b1f340b62726edc33b3e7e05d52634c2a2595b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut ist extern sichtbar.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn eine Assembly mit Component Object Model (COM) registriert ist, werden Einträge in der Registrierung für jede in der Assembly für COM sichtbarer Typ hinzugefügt. Mit markierte Methoden der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> und <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> Attribute heißen während der Registrierung und Aufhebung der Registrierung, um die Ausführung von Benutzercode, der speziell für die Registrierung/Aufhebung der Registrierung dieser Typen ist. Dieser Code sollte nicht außerhalb dieser Prozesse aufgerufen werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff für die Methode `private` oder `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Methoden, die diese Regel verletzen.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrieren von Assemblys bei COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)