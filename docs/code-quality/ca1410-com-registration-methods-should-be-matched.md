---
title: 'CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bca9e06c861ab2bcaceead8bf8ee195b64e45c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234734"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen.

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ deklariert eine Methode, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> -Attribut markiert ist, aber keine Methode deklariert, die mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut markiert ist, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung

Damit Component Object Model (com)-Clients einen .NET-Typ erstellen können, muss der Typ zuerst registriert werden. Wenn Sie verfügbar ist, wird eine Methode, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> -Attribut markiert ist, während des Registrierungsvorgangs aufgerufen, um benutzerdefinierten Code auszuführen. Eine entsprechende-Methode, die mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> -Attribut markiert ist, wird während der Aufhebung der Registrierung aufgerufen, um die Vorgänge der Registrierungsmethode umzukehren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Registrierung oder Aufhebung der Registrierung hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Der kommentierte Code zeigt die Korrektur des Verstoßes.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Assemblys bei com registrieren](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)