---
title: 'CA1410: COM-Registrierungsmethoden müssen übereinstimmen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1701ac1a432a9957e4350601ea55f13c6371147d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872894"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM-Registrierungsmethoden müssen übereinstimmen.

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut deklariert jedoch keine Methode, die mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung
 Für Clients Component Object Model (COM) zum Erstellen von .NET Framework-Typ muss der Typ zuerst registriert werden. Wenn sie verfügbar ist, eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> -Attribut während der Registrierung zum Ausführen benutzerdefinierter Code aufgerufen wird. Eine entsprechende Methode, die mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> -Attribut aufgerufen wird, bei der Aufhebung der Registrierung, der die Vorgänge von der Registrierungsmethode umzukehren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Registrierung oder das Aufheben der Registrierung-Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Kommentierte Code zeigt das Update für die Verletzung.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrieren von Assemblys bei COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Assembly Registration-Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)