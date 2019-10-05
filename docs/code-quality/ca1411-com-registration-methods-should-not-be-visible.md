---
title: 'CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.'
ms.date: 11/04/2016
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
ms.openlocfilehash: e9582fb6bbdbda8aefbb60e2c69d16380eec3dff
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234748"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> -Attribut oder dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut markiert ist, ist extern sichtbar.

## <a name="rule-description"></a>Regelbeschreibung
Wenn eine Assembly mit Component Object Model (com) registriert wird, werden der Registrierung für jeden COM-sichtbaren Typ in der Assembly Einträge hinzugefügt. Methoden, die mit dem- <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> Attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> und dem-Attribut markiert sind, werden während der Registrierungs-bzw. der Aufhebung der Registrierung aufgerufen, um Benutzercode auszuführen, der für die Registrierung/Aufhebung der Registrierung dieser Typen spezifisch ist. Dieser Code sollte nicht außerhalb dieser Prozesse aufgerufen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, `private` ändern Sie den Zugriff der-Methode in oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] `internal` (`Friend` in).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt zwei Methoden, die gegen die Regel verstoßen.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1410: COM-Registrierungsmethoden müssen abgeglichen werden](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrieren von Assemblys bei COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)