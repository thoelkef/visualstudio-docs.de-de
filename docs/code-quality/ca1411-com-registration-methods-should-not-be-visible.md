---
title: 'CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 39547159f46f4c1921093b020c2bb888e4aecce0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013170"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut ist als extern sichtbar.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine Assembly mit Component Object Model (COM) registriert ist, werden die Einträge in der Registrierung für jede in der Assembly für COM sichtbarer Typ hinzugefügt. Mit markierte Methoden der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> und <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> Attribute werden aufgerufen, während der Registrierung und Aufhebung der Registrierung, um bei der Ausführung von Benutzercode, der spezifisch für die Registrierung/Aufhebung der Registrierung dieser Typen ist. Dieser Code sollte nicht außerhalb dieser Prozesse aufgerufen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff auf die Methode, die `private` oder `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, die die Regel verletzen.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1410: COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrieren von Assemblys bei COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)