---
title: 'CA1410: COM-Registrierungsmethoden abgeglichen werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ deklariert eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> -Attribut deklariert jedoch keine Methode, die mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut, oder umgekehrt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Für Clients von Component Object Model (COM) zum Erstellen einer [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Typ, der Typ muss zuerst registriert werden. Falls er verfügbar ist eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> -Attribut bei der Registrierung zum Ausführen benutzerdefinierter Code aufgerufen wird. Eine entsprechende Methode, die mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> -Attribut aufgerufen wird, während die Aufhebung der Operationen der Registrierungsmethode Reihenfolge umgekehrt werden soll.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Registrierung oder der Aufhebung der Registrierung-Methode hinzu.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt. Der kommentierte Code zeigt die Lösung einer Verletzung.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrieren von Assemblys bei COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)