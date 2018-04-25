---
title: 'CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 216b500d243a0ffd51cd98e55f28b847c9804f4d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
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
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrieren von Assemblys mit COM](/dotnet/framework/interop/registering-assemblies-with-com) [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)