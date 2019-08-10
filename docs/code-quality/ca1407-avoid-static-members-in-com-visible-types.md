---
title: 'CA1407: Statische Member in für COM sichtbaren Typen vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631be1a93318cd24af4251fefbc710294fa52bf7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922011"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Statische Member in für COM sichtbaren Typen vermeiden.

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Typ, der speziell für Component Object Model (com) als sichtbar gekennzeichnet ist, `public``static` enthält eine-Methode.

## <a name="rule-description"></a>Regelbeschreibung
COM unterstützt `static` keine Methoden.

Diese Regel ignoriert Eigenschafts-und Ereignisaccessoren, Operator Überladungsmethoden oder Methoden, die entweder mit <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> dem-Attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> oder dem-Attribut markiert sind.

Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen.

Damit diese Regel <xref:System.Runtime.InteropServices.ComVisibleAttribute> auftritt, muss auf `false` Assemblyebene der Wert festgelegt werden, und <xref:System.Runtime.InteropServices.ComVisibleAttribute> die-Klasse muss `true`auf festgelegt werden, wie im folgenden Code gezeigt.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass eine Instanzmethode verwendet wird, `static` die dieselbe Funktionalität wie die-Methode bereitstellt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn ein com-Client keinen Zugriff auf die Funktionen benötigt, die `static` von der-Methode bereitgestellt werden.

## <a name="example-violation"></a>Beispiel Verstoß

### <a name="description"></a>Beschreibung
Das folgende Beispiel zeigt eine `static` Methode, die gegen diese Regel verstößt.

### <a name="code"></a>Code
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Kommentare
In diesem Beispiel kann die **Book. FromPages** -Methode nicht von com aufgerufen werden.

## <a name="example-fix"></a>Beispiel Korrektur

### <a name="description"></a>Beschreibung
Um die Verletzung im vorherigen Beispiel zu beheben, können Sie die Methode in eine Instanzmethode ändern, aber dies ist in dieser Instanz nicht sinnvoll. Eine bessere Lösung besteht darin, explizit `ComVisible(false)` auf die-Methode anzuwenden, um anderen Entwicklern zu helfen, dass die Methode von com nicht angezeigt werden kann.

Das folgende Beispiel gilt <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> für die-Methode.

### <a name="code"></a>Code
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Siehe auch
[Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)